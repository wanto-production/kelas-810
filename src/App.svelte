<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Nav from './lib/nav.svelte';
  import './app.css'
  import { animate,stagger } from 'motion'
  import { onMount } from 'svelte'

  let [members,letters,text] = [[],[],''];

  onMount(()=>{
    animate(letters,
      {y:[0,10,-10,0]},
      {duration:1,delay: stagger(0.1),repeat:Infinity}
    )
    fech()
  })

  function fech() {
    const existingmember = localStorage.getItem('member');
    if (existingmember) {
      members = JSON.parse(existingmember);
    }else{
      members = [];
    }
  }

  function addmember() {
    members = [...members,text]
    localStorage.setItem('member',JSON.stringify(members))
    text = ''
  }
</script>

<main>
<Nav/>
<section id="home" class=" w-full h-screen flex justify-center gap-5 items-center bg-[url(./night.jpg)] bg-cover bg-center bg-no-repeat bg-fixed flex-wrap pl-3 pr-3">
  <img data-aos="fade-right" src="./profil.jpeg" alt="" class=" h-auto w-72 rounded-md cursor-pointer">
  <div class=" h-[200px]">
    <h1 data-aos="fade-left" class="text-3xl font-bold text-white flex">
      {#each 'hello_class_810'.split('') as letter,i}
        <span class=" inline-block" bind:this={letters[i]}>{letter}</span>
      {/each}
    </h1>
    <p data-aos="fade-left" data-aos-delay="300" class=" text-2xl text-white mt-3">sahabat selamanya saling sep tolong menolong</p>
  </div>
</section>
<section id="member" class=" w-full h-screen bg-black border-t-4 border-blue-600 flex justify-center flex-col items-center gap-2">
  <h1 data-aos="fade-down" data-aos-delay="400" class=" text-white text-2xl">nama nama member cik</h1>
<div class="w-[350px] h-[380px] flex justify-center items-center relative">

    <!-- Underlying Gradient Div-->
    <div class="absolute w-full h-full inset-0 rounded-lg bg-gradient-to-br from-pink-500 via-cyan-500 to-violet-500"></div>

    <!-- Our Main Div --- We use relative here so it shows above the gradient div-->
    <div class="relative w-[96%] min-h-[96%] h-fit bg-black rounded-lg p-4 overflow-y-scroll flex gap-2 flex-col">
      <!-- Loop through our members array -->
       {#if members.length > 0}
          {#each members as item,i }
            <li data-aos="fade-right" class=" list-none text-2xl text-white">{i+1}. {item}</li>
          {/each}
       {:else}
       <div class=" w-full h-full flex justify-center items-center">
         <p data-aos="flip-up" data-aos-delay="400" class=" text-white">Belum ada member lho ya</p>
       </div>
       {/if}
    </div>
</div>
<form class=" mt-2" on:submit|preventDefault={addmember}>
  <input class=" p-3 focus:outline-none rounded-s-md placeholder:text-black w-[250px]" type="text" bind:value={text} placeholder="tambah(gabisa di hapus lho ya)" required/>
  <button class=" bg-blue-600 text-white p-3 rounded-e-md" type="submit">submit</button>
</form>
</section>
<div class="pt-12 flex gap-4 flex-wrap items-center justify-center w-full min-h-[300px] h-fit bg-[url(/nature.jpg)] bg-center bg-cover bg-no-repeat bg-fixed border-t-4 border-blue-600">
  <div class=" w-[300px] h-[200px] backdrop-blur-2xl border-2 border-blue-500 rounded-md p-1 mb-4">
  <h1 class=" text-white font-bold text-2xl">framework yang gw gunakan</h1>
  <div class="flex gap-4 justify-center items-center mt-4">
    <img src={svelteLogo} alt="svelte logo" class="w-[100px] h-[100px]"/>
    <img src={viteLogo} alt="vite logo" class="w-[100px] h-[100px]"/>
  </div>
  </div>
  <div class=" w-[300px] h-[200px] backdrop-blur-2xl border-2 border-blue-500 rounded-md p-1 mb-4">
    <h1 class=" text-white font-bold text-2xl">image i use</h1>
    <div class=" w-full flex justify-center items-center h-full">
      <a href="https://unsplash.com/">
        <img class=" w-auto h-[100px] rounded-md" src="data:image/png;base64,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" alt="">
      </a>
    </div>
  </div>
</div>
</main>