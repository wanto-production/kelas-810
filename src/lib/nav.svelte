<script>
    import svelteLogo from '../assets/svelte.svg'
</script>

<div class=" w-full h-[50px] fixed top-0 flex items-center justify-around shadow-md shadow-orange-600 backdrop-blur-xl z-10">
    <div class=" flex flex-row gap-2 items-center">
        <img src={svelteLogo} alt="svelte logo" class="w-[30px] h-auto object-cover"/>
        <h1 class=" text-orange-700 font-bold text-3xl">class 8 10</h1>
    </div>
    <ul class=" flex flex-row gap-4 w-fit">
      <li><a href="#home" class=" text-white relative text-xl w-fit block after:block after:content-[''] after:absolute after:h-[3px] after:bg-white after:w-full after:scale-x-0 after:hover:scale-x-100 after:transition after:duration-300 after:origin-right">home</a></li>
      <li><a href="#member" class=" text-white relative text-xl w-fit block after:block after:content-[''] after:absolute after:h-[3px] after:bg-white after:w-full after:scale-x-0 after:hover:scale-x-100 after:transition after:duration-300 after:origin-right">member</a></li>
    </ul>
</div>