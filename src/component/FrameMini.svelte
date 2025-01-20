<script>
    export let imageSrc;
    export let title = "image";
    export let description;
    export let price;
    export let material;
    export let size;
    export let href;
</script>

<a href={href} class="block p-4 bg-white rounded-lg shadow-md hover:shadow-lg overflow-hidden transition-shadow duration-150  mx-3 border">
    <img src={imageSrc} alt={title} class="w-full h-48 object-cover mb-4" />
    <h2 class="text-lg font-semibold mb-2">{title}</h2>
    <p class="text-gray-600">
        <span>Price: </span><span class="font-semibold">${price.toFixed(2)}</span><br />
        <span>Material: </span><span class="font-semibold">{material}</span><br />
        <span>Size: </span><span class="font-semibold">{size}</span><br />
        {description}
    </p>
</a>