<script>
    import FrameMini from "../../component/FrameMini.svelte";
    import Header from "../Header.svelte";

    let selectedOption = 'Casual'; // Default selected option
    let products = []; // Array to store products based on selection

    // Static product data
    // const allProducts = [
    //     {
    //         id: "1",
    //         name: "Casual Shirt",
    //         category: "Casual",
    //         price: 29.99,
    //         image: "https://imgs.search.brave.com/CF7ne71qw8fmijGT0M4242-FTF0TVmqppmoplecH_14/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9tLm1l/ZGlhLWFtYXpvbi5j/b20vaW1hZ2VzL0kv/NzEwVDdvcmRvZEwu/anBn",
    //         material: "Cotton",
    //         size: "M",
    //         link: "#"
    //     },
    //     {
    //         id: "2",
    //         name: "Formal Suit",
    //         category: "Formal",
    //         price: 99.99,
    //         image: "https://imgs.search.brave.com/2UdIDeLW_lPZwsu61s-qpR_2JQ8pPBY4vFDk71za-ok/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9tLm1l/ZGlhLWFtYXpvbi5j/b20vaW1hZ2VzL0kv/NzF5Nkx4WmljbEwu/anBn",
    //         material: "Wool",
    //         size: "L",
    //         link: "#"
    //     },
    //     {
    //         id: "3",
    //         name: "Sports Jacket",
    //         category: "Sports",
    //         price: 49.99,
    //         image: "https://imgs.search.brave.com/qMFhxdXxL4kGLwKVM8HRsV5sWw0FXSkDC9cga1BMR3U/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9tLm1l/ZGlhLWFtYXpvbi5j/b20vaW1hZ2VzL0kv/NzFrSDBsZjVvQ0wu/anBn",
    //         material: "Polyester",
    //         size: "M",
    //         link: "#"
    //     },
    //     // Add more products as needed
    // ];

    const allProducts = [];

    function generateProduct(id) {
    const categories = ["Casual", "Formal", "Sports"];
    const materials = ["Cotton", "Wool", "Polyester", "Nylon", "Leather"];
    const sizes = ["XS", "S", "M", "L", "XL"];

    return {
        id: id.toString(),
        name: `${categories[Math.floor(Math.random() * categories.length)]} ${Math.random().toString(36).substring(2, 7)}`,
        category: categories[Math.floor(Math.random() * categories.length)],
        price: Math.floor(Math.random() * (100 - 20) + 20), // Random price between $20 and $100
        image: `https://picsum.photos/200?random=${id}`, // Random image from Unsplash
        material: materials[Math.floor(Math.random() * materials.length)],
        size: sizes[Math.floor(Math.random() * sizes.length)],
        link: "#",
    };
    }

    for (let i = 0; i < 20; i++) {
    allProducts.push(generateProduct(i + 1));
    }


    const handleOptionChange = (event) => {
        selectedOption = event.target.value;
    };

    function handleButtonClick() {
        // Filter products based on the selected category
        products = allProducts.filter(product => product.category === selectedOption);
    }
</script>

<div class="bg-white text-black">
    <Header />
    <div class="max-w-screen-xl mx-auto px-4 py-16 ">
        <h1 class="text-4xl font-bold text-center mb-8">MEN</h1>

        <div class="flex justify-center mb-8">
            <select
                class="border border-gray-300 p-2 rounded"
                on:change={handleOptionChange}
            >
                <option value="Casual">Casual</option>
                <option value="Formal">Formal</option>
                <option value="Sports">Sports</option>
            </select>
            <button 
                on:click={handleButtonClick} 
                class="ml-4 bg-blue-500 text-white p-2 rounded"
            >
                Show Products
            </button>
        </div>

        {#if products.length > 0}
            <p>You selected {selectedOption}.</p>
            <div class="py-5 px-2 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
                {#each products as product}
                    <FrameMini 
                        imageSrc={product.image} 
                        title={product.name} 
                        description={product.description || "No description available."} 
                        price={product.price} 
                        material={product.material} 
                        size={product.size} 
                        href={product.link} 
                    />
                {/each}
            </div>
        {:else if products.length === 0}
            <p>No products available for {selectedOption}.</p>
        {/if}
    </div>
</div>