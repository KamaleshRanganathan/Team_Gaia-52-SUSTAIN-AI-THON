<!-- Bot to help me purchase -->


<script>
    import { onMount } from 'svelte';
    
  
    let products = [];
  
    const generateRandomProducts = () => {
      const categories = ['Electronics', 'Clothing', 'Books', 'Home', 'Food'];
      const randomProducts = [];
  
      for (let i = 0; i < 10; i++) {
        const randomCategory = categories[Math.floor(Math.random() * categories.length)];
        randomProducts.push({
          id: i + 1,
          name: `Product ${i + 1}`,
          description: `This is the description for Product ${i + 1}`,
          price: Math.floor(Math.random() * 100) + 1, 
          category: randomCategory,
          imageUrl: `https://via.placeholder.com/150` 
        });
      }
  
      return randomProducts;
    };
  
    onMount(() => {
      products = generateRandomProducts(); 
    });
  
    const getGeminiPrompt = () => {
      if (products.length === 0) {
        return 'Please generate products first.';
      }
  
      const prompt = `
        Here are some product details:
        ${products.map(product => 
          `- **Name:** ${product.name}\n` +
          `  **Description:** ${product.description}\n` +
          `  **Price:** ${product.price}\n` +
          `  **Category:** ${product.category}\n` +
          `  **Image URL:** ${product.imageUrl}\n` 
        ).join('\n\n')}
  
        **Prompt:** [Your prompt here, e.g., "Write a compelling product description for Product 1."]`;
  
      return prompt;
    };
  </script>
  
  <button on:click={() => products = generateRandomProducts()}>Generate Random Products</button>
  
  <div>
    {#if products.length > 0}
      <p>Generated Products:</p>
      <ul>
        {#each products as product}
          <li>{product.name} - {product.category}</li>
        {/each}
      </ul>
    {/if}
  </div>
  
  <div>
    <p>Gemini Prompt:</p>
    <!-- svelte-ignore element_invalid_self_closing_tag -->
    <textarea value={getGeminiPrompt()} rows={10} cols={50} readOnly />
  </div>