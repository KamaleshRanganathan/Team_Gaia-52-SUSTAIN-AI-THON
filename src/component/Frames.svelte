<script>
    export let imageSrc;
    export let title;
    export let description;
    export let href;
</script>

<a href="{href}" class="block p-4 bg-white rounded-lg shadow-md hover:shadow-lg overflow-hidden transition-shadow duration-150 w-1/3 mx-3 border">
    <img src={imageSrc} alt={title} class="w-full h-48 object-cover mb-4" />
    <h2 class="text-lg font-semibold mb-2">{title}</h2>
    <p class="text-gray-600">{description}</p>
</a>