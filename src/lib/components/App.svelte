<script lang="ts">
  import { Canvas } from '@threlte/core'
  import Scene from './Scene.svelte'
  import AutoText from './AutoText.svelte'
  
</script>

<div class = "canvas-container">
  <header class="flex items-center justify-start p-4">
    <img src="/mimes-logo-white.png" alt="Logo" class="h-10">
  </header>
  
  
  <Canvas>
    <Scene />
  </Canvas>
  
  <div class="overlay-content">
    <div>
      <div class='flex w-full flex-col justify-center p-5 text-center md:w-full md:text-center'>
        <h1 class='my-4 text-5xl font-bold leading-tight text-center'>Animate Your World</h1>
        <p class='mb-8 text-2xl leading-normal'>Easily Create 3D Characters and Scenes</p>
      </div>
    </div>
    <div class="mx-auto flex w-full flex-col flex-wrap items-center justify-center md:flex-row px-2 lg:w-4/5">
      <form action="https://api.web3forms.com/submit" method="POST">
  
        <input type="hidden" name="access_key" value="928aa7e4-7d32-42bc-a8c7-c82154345c8c" />
      
        <div class="flex space-x-2"> <!-- Flex container -->
          <input
            class='border-2 border-gray-300 p-2 flex-1'
            type="text"
            name="name"
            placeholder='Your name'
            required
          />
          <input
            class='border-2 border-gray-300 p-2 flex-1'
            type="email"
            name="email"
            placeholder='Your email'
            required
          />
        </div>
      
        <input type="hidden" name="redirect" value="https://web3forms.com/success" />
        <button class='bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 my-2 px-4 rounded w-full'
          type="submit">Sign Up for Beta Access</button>
      
      </form>
     
    </div> 
  </div>  
  <AutoText />  
</div>





<style>
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  .canvas-container {
    position: relative;
    width: 100%; 
    height: 100%; 
  }

  .overlay-content {
    position: absolute;
    top: 25%; /* Center vertically */
    left: 50%; /* Center horizontally */
    transform: translate(-50%, -50%); /* Adjust for the element's own size */
    color: white;
    z-index: 10; /* Ensure it's above the canvas */
  }


  h1 {
    font-family: 'Roboto', sans-serif;
    color: white;
    margin: 0;
    padding: 0;
    text-align: center;
    font-size: 3em;
  }  

  input {
    font-size: 1.2em;
    border: 2px solid #333;
    padding: 0.5em;
  }  
</style>



