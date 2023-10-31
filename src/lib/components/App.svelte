<script lang="ts">
  import { Canvas } from '@threlte/core'
  import Scene from './Scene.svelte'
  import AutoText from './AutoText.svelte';
  import { Jumper } from 'svelte-loading-spinners';

  const sentences = [
    "a spiderman walking",
    "a princess casting a spell",
    "a psychedelic old wizard walking",
    "a catwoman doing karate",
    "a film noir hulk walking clumsily",
  ];

  let currentCharacter = null; // No default character

  // Function to determine which character to show based on the sentence
  function updateCharacter(sentence) {
    if (sentence === "a spiderman walking") {
      currentCharacter = 'Spiderman';
    } else if (sentence === "a princess casting a spell") {
      currentCharacter = 'Princess';
    } else if (sentence === "a psychedelic old wizard walking") {
      currentCharacter = 'Wizard';
    } else if (sentence === "a catwoman doing karate") {
      currentCharacter = 'CatWoman';
    } else if (sentence === "a film noir hulk walking clumsily") {
      currentCharacter = 'Hulk';
    }
  }
</script>

<div class = "canvas-container">
  <header class="flex items-center justify-start p-4">
    <img src="/mimes-logo-white.png" alt="Logo" class="h-10">
  </header>
  
  {#if currentCharacter === null}
    <div class="loading-spinner">
      <Jumper size="60" color="#80c8ff" unit="px" duration="1s" />
    </div>
  {:else}
    <Canvas>
      <Scene {currentCharacter} />
    </Canvas>
  {/if}
  
  <div class="overlay-content">
    <div>
      <div class='flex w-full flex-col justify-center p-0 sm:p-5 text-center md:w-full md:text-center mt-10 sm:mt-0'>
        <h1 class='my-4 text-3xl sm:text-4xl md:text-5xl font-bold leading-tight text-center'>Animate Your World</h1>
        <p class='mb-8 text-xl sm:text-2xl md:text-3xl leading-normal'>Create 3D Characters and Scenes with AI</p>
      </div>      
    </div>
    <div class="mx-auto flex w-full flex-col flex-wrap items-center justify-center md:flex-row px-2 lg:w-4/5">
      <form action="https://api.web3forms.com/submit" method="POST">
  
        <input type="hidden" name="access_key" value="928aa7e4-7d32-42bc-a8c7-c82154345c8c" />
      
        <div class="flex flex-col sm:flex-row space-y-2 sm:space-y-0 sm:space-x-2"> <!-- Responsive flex container -->
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
  <AutoText {sentences} on:typingFinished={e => updateCharacter(e.detail)} />
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

  .loading-spinner {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 20; 
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
  }  

  input {
    font-size: 1.2em;
    border: 2px solid #333;
    padding: 0.5em;
    color: black;
    &:hover {
      border: 2px solid rgb(0, 195, 255);
    }
  }  
</style>



