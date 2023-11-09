<script lang="ts">
  import { T, useFrame } from '@threlte/core'
  import { Grid, OrbitControls } from '@threlte/extras'
  import Spiderman from '$lib/components/models/spiderman.svelte'
  import Wizard from '$lib/components/models/wizard-color.svelte'
  import Princess from '$lib/components/models/princess-spell.svelte'    
  import CatWoman from '$lib/components/models/catwoman-karate.svelte'    
  import Hulk from '$lib/components/models/hulk-filmnoir.svelte'  
  import Skyline from '$lib/components/models/skyline.svelte'

  let actions: any;
  export let currentCharacter = null; // Receive the current character as a prop

  // State variables for position and movement direction
  let position = [0, 1, 0];
  let moveDirection = { forward: 0, backward: 0, left: 0, right: 0 };

  // Event handlers for W, A, S, D keys
  function onKeyDown(e: KeyboardEvent) {
    switch (e.key) {
        case 'w':
        case 'W':
            moveDirection.forward = 1;
            break;
        case 's':
        case 'S':
            moveDirection.backward = 1;
            break;
        case 'a':
        case 'A':
            moveDirection.left = 1;
            break;
        case 'd':
        case 'D':
            moveDirection.right = 1;
            break;
    }
  }

  function onKeyUp(e: KeyboardEvent) {
    switch (e.key) {
        case 'w':
        case 'W':
            moveDirection.forward = 0;
            break;
        case 's':
        case 'S':
            moveDirection.backward = 0;
            break;
        case 'a':
        case 'A':
            moveDirection.left = 0;
            break;
        case 'd':
        case 'D':
            moveDirection.right = 0;
            break;
    }
  }

  // Update position of the GLB model based on movement direction
  useFrame(() => {
    if (moveDirection.forward) position[2] -= 0.1;
    if (moveDirection.backward) position[2] += 0.1;
    if (moveDirection.left) position[0] -= 0.1;
    if (moveDirection.right) position[0] += 0.1;
  });

  $: {
    // console.log($actions)
    $actions?.animation?.play()
  }
</script>

<svelte:window on:keydown={onKeyDown} on:keyup={onKeyUp} />

<T.PerspectiveCamera
  makeDefault
  position={[-10, 2, 20]}
  fov={15}
>
  <OrbitControls
    enableZoom={false}
    enableDamping
    target.y={1.5}
  />
</T.PerspectiveCamera>

<T.DirectionalLight
  intensity={0.8}
  position.x={0}
  position.y={1}
/>
<T.AmbientLight intensity={0.5} />

<Grid
  position.y={-0.001}
  cellColor="#ffffff"
  sectionColor="#ffffff"
  sectionThickness={0}
  fadeDistance={25}
  cellSize={2}
/>

<!-- Conditionally render the character based on the currentCharacter prop -->
{#if currentCharacter === 'Spiderman'}
  <Spiderman bind:actions {position} />
{:else if currentCharacter === 'Princess'}
  <Princess bind:actions {position} />
{:else if currentCharacter === 'Wizard'}
  <Wizard bind:actions {position} />
{:else if currentCharacter === 'CatWoman'}
  <CatWoman bind:actions {position} />
{:else if currentCharacter === 'Hulk'}
  <Hulk bind:actions {position} />
{/if}
<Skyline/>