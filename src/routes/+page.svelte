<script>
  import Header from "./Header.svelte";
  import Footer from "./Footer.svelte";
	import Frames from "../component/Frames.svelte";

  const img ="https://imgs.search.brave.com/vdG6Ujqga972ibziYpYjZSaRC8lxgjTv-1T2n08aBUQ/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly90My5m/dGNkbi5uZXQvanBn/LzAyLzE3LzczLzM2/LzM2MF9GXzIxNzcz/MzYxNV9KeFlIZWZn/ejBKQmNGcUREVVRl/S29MZkI0S25RbDFO/di5qcGc";
  </script>

<Header class="fixed " />
<div class="min-h-screen bg-white text-black">
  <div class="relative text-center border border-b-base-content border-t-transparent pt-28 pb-20"> 
    <!-- svelte-ignore a11y_img_redundant_alt -->
    <img src={img} alt="Descriptive Image Text" class="absolute inset-0 object-cover w-full h-full opacity-100" /> 
    <div class="relative z-10"> 
      <p class="font-bold text-8xl md:text-7xl sm:text-6xl">Dress Sustainably </p><br> <br>
      <p class="font-bold text-6xl md:text-5xl sm:text-4xl"> Your Guide to <span class="text-green-500">Eco</span>-Friendly Fashion</p>
      <p class="font-semibold text-4xl md:text-3xl sm:text-2xl mt-20">Find sustainable clothing, learn about eco-friendly materials, and make informed choices.</p>
    </div>
  </div>
  <div class="mt-10 ml-10 pb-10 text-center text-xl font-semibold">
    <a href="./">
      <button class="bg-blue-500 hover:bg-blue-700 text-white  py-2 px-4 rounded w-2/3">
        View all Products
      </button>
    </a>
    <div class="flex flex-row">
      <Frames imageSrc="https://i.pinimg.com/474x/c8/03/74/c803748d3cea46a5fb113b9199806f13.jpg" title="MEN" description="" href="./men" />
      <Frames imageSrc="https://imgs.search.brave.com/aUOiyvt-0vEnzPVTex7l9kcqoTrXeI7j6Vre3Jpy54Q/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9pLnBp/bmltZy5jb20vb3Jp/Z2luYWxzL2ZhLzEx/L2FkL2ZhMTFhZDgx/ZjRmOGQ1MWZkZWZj/NGNmMzk4NDkxY2Rm/LmpwZw" title="WOMEN" description="" href="./women"/>
      <Frames imageSrc="https://imgs.search.brave.com/k7cZ9bhjLkFArnGtLcAOHgZO5jBNtVLEyzV9DP7ZjMI/rs:fit:860:0:0:0/g:ce/aHR0cHM6Ly9tZWRp/YS5pc3RvY2twaG90/by5jb20vaWQvODMy/NjY2MzkvcGhvdG8v/eW91bmctYm95LWp1/bXBpbmctaW4tbWlk/LWFpci5qcGc_cz02/MTJ4NjEyJnc9MCZr/PTIwJmM9NVMzY0Uw/aGNrWk9oZXJ0Tl9t/dEVfeXNHM1VpeFE3/U3FLZjFMcC1DSjY1/QT0" title="KIDS" description="" href="./kids" />    
    </div>
  </div>
  
  
  <!-- <div class="text-left mt-10 ml-10 pb-10">
    <h1 class="text-4xl md:text-3xl sm:text-2xl">Why Sustainable Choices Matter ?</h1> 
    <div class="container  px-4">
      <h2 class="text-3xl md:text-2xl sm:text-xl font-bold mb-4">The Fast Fashion Problem:</h2>
      <ul class="list-disc ml-6">
        <li class="mb-2">Environmental Impact:</li>
        <ul class="list-disc ml-6">
          <li class="mb-1">Resource Depletion: High water and energy consumption, deforestation for materials.</li>
          <li class="mb-1">Pollution: Chemical dyes polluting waterways, microplastics from synthetic fabrics.</li>
          <li>Waste: Massive textile waste in landfills, contributing to environmental degradation.</li>
        </ul>
        <li class="mb-2">Social Impact:</li>
        <ul class="list-disc ml-6">
          <li class="mb-1">Exploitative Labor: Low wages, unsafe working conditions, and unfair treatment of garment workers.</li>
          <li>Unethical Practices: Support of unsustainable farming methods and harmful chemical use.</li>
        </ul>
      </ul>
    
      <h2 class="text-3xl md:text-2xl sm:text-xl font-bold mt-8">Benefits of Sustainable Fashion:</h2>
      <ul class="list-disc ml-6">
        <li class="mb-2">Reduced Environmental Impact:</li>
        <ul class="list-disc ml-6">
          <li class="mb-1">Lower carbon footprint: Using renewable energy, minimizing transportation distances.</li>
          <li class="mb-1">Water conservation: Employing water-efficient dyeing and finishing techniques.</li>
          <li>Reduced waste: Promoting circular economy practices like recycling and upcycling.</li>
        </ul>
        <li class="mb-2">Social Responsibility:</li>
        <ul class="list-disc ml-6">
          <li class="mb-1">Fair labor practices: Ensuring fair wages, safe working conditions, and ethical treatment of workers.</li>
          <li class="mb-1">Supporting local communities: Sourcing materials and producing goods locally whenever possible.</li>
          <li>Transparency: Providing consumers with information about the entire supply chain.</li>
        </ul>
      </ul>
    </div>
  </div> -->
</div>
<Footer/>