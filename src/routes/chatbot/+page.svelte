<script>
    import Header from "../Header.svelte";
    import { GoogleGenerativeAI } from "@google/generative-ai";
    import PromptText from "./promptText.svelte"; 
    import Footer from "../Footer.svelte";

    const gemini_key = "AIzaSyBzfND6pFGFSxe9zN9T2823Y8hGG-2Y6NE"; 
    let genAI; 
    let model;
    let chat; 
    let promptText = "";
    let isSubmitting = false; 
    let chatHistory = [
        { id: crypto.randomUUID(), role: "ChatBot", text: " Welcome to the chat! How can I assist you today?" }
    ];

    $: {
      if (gemini_key) {
        genAI = new GoogleGenerativeAI(gemini_key);
        model = genAI.getGenerativeModel({ model: "gemini-1.5-flash" });
        chat = model.startChat({
          history: [
            { role: "user", parts: [{ text: "Hello" }] },
            { role: "model", parts: [{ text: "Great to meet you. What would you like to know?" }] },
          ],
        });
      }
    }

    async function query() {
      if (chat && promptText !== "" && !isSubmitting) { 
        isSubmitting = true; 
        try {
          let result = await chat.sendMessage(promptText); 

          chatHistory = [
            ...chatHistory, 
            { 
              id: crypto.randomUUID(), 
              role: "user", 
              text: promptText 
            },
            { 
              id: crypto.randomUUID(), 
              role: "ChatBot", 
              text: result.response.text() 
            }
          ];

          promptText = ""; 
        } catch (error) {
          console.error("Error:", error); 
          alert("An error occurred."); 
        } finally {
          isSubmitting = false; 
        }
      } else if (!chat) {
        alert("Chat not initialized."); 
      } else if (promptText === "") {
        alert("Please enter a query."); 
      }
    }
</script>

<Header />

<div class="min-h-screen flex flex-col bg-accent text-accent-content text-lg">
    <div class="flex flex-col w-3/4 m-auto  my-5 ">
        <!-- svelte-ignore a11y_label_has_associated_control -->
        <label class="">Enter your Query Here:</label>
        <div>
            <input 
                type="text" 
                class="rounded bg-primary-content text-white p-2 h-10 w-10/12 focus:outline-none focus:ring-2 focus:ring-blue-500" 
                placeholder="Enter your message" 
                bind:value={promptText} 
            />
            <button 
                on:click={query} 
                class={`bg-primary-content
                        text-primary
                        ${promptText.trim() !== '' && !isSubmitting ? 'bg-blue-500 hover:bg-blue-600' : 'bg-primary-content text-primary cursor-not-allowed'} 
                        rounded 
                        p-2 
                        transition-colors 
                        duration-200`} 
            >
                Submit
            </button>
        </div>
    </div>

    <div class="w-3/4 m-auto flex-grow overflow-y-auto">
        {#each chatHistory.slice().reverse() as { id, role, text }}
            <PromptText id={id} role={role} textContent={text} /> 
        {/each}
    </div>

    <Footer class="fixed bottom-0 left-0 w-full" />
</div>