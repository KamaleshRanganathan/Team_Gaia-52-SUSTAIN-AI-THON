<script>
    import Footer from "../Footer.svelte";
import Header from "../Header.svelte";
  
    let name = '';
    let email = '';
    let clothImage = '';
    let clothType = '';
    let address = '';
    let donationId = '';
  
    // Function to generate a unique ID
    function generateId() {
      return 'donation-' + Math.random().toString(36).substr(2, 9);
    }
  
    // Handle form submission
    function handleSubmit(event) {
      event.preventDefault();
      donationId = generateId(); // Generate a new ID on submission
      console.log('Donation Details:', {
        name,
        email,
        clothImage,
        clothType,
        address,
        donationId
      });
      name = '';
      email = '';
      clothImage = '';
      clothType = '';
      address = '';
      // Here you can add logic to send the data to your server or API
    }
  </script>
  
  <Header />
  
  <div class="flex items-center justify-center min-h-screen bg-secondary text-secondary-content"> 
    <form on:submit={handleSubmit} class="w-1/4 p-6 bg-white rounded-lg shadow-md">
      <h2 class="text-2xl font-bold mb-4 text-center">Donate Clothes</h2>
  
      <div class="space-y-4"> 
        <div>
          <label for="name" class="block text-sm font-medium text-gray-700">Name:</label>
          <input 
            id="name" 
            type="text" 
            bind:value={name} 
            required 
            class="mt-1 block w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-500" 
          />
        </div>
  
        <div>
          <label for="email" class="block text-sm font-medium text-gray-700">Email:</label>
          <input 
            id="email" 
            type="email" 
            bind:value={email} 
            required 
            class="mt-1 block w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-500" 
          />
        </div>
  
        <div>
          <label for="clothImage" class="block text-sm font-medium text-gray-700">Cloth Image URL:</label>
          <input 
            id="clothImage" 
            type="text" 
            bind:value={clothImage} 
            required 
            class="mt-1 block w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-500" 
          />
        </div>
  
        <div>
          <label for="clothType" class="block text-sm font-medium text-gray-700">Cloth Type:</label>
          <input 
            id="clothType" 
            type="text" 
            bind:value={clothType} 
            required 
            class="mt-1 block w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-500" 
          />
        </div>
  
        <div>
          <label for="address" class="block text-sm font-medium text-gray-700">Address:</label>
          <input 
            id="address" 
            type="text" 
            bind:value={address} 
            required 
            class="mt-1 block w-full p-2 border border-gray-300 rounded-md focus:outline-none focus:ring focus:ring-blue-500" 
          />
        </div>
      </div>
  
      <button 
        type="submit" 
        class="mt-6 w-full bg-green-500 text-white p-2 rounded-md hover:bg-green-600 transition duration-150"
      >
        Submit Donation
      </button>
  
      {#if donationId}
        <p class="mt-4 text-center text-green-600">Your donation ID is: {donationId}</p>
      {/if}
    </form>
  </div>
  <Footer/>