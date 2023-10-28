<script lang="ts">
  import App from '$lib/components/App.svelte'
</script>

<div>  
  <App />
</div>

<style>
  :global(body) {
    margin: 0;
  }

  div {
    width: 100vw;
    height: 100vh;
    background: rgb(59, 88, 150);
    background: linear-gradient(180deg, rgba(59, 88, 150) 0%, rgba(8, 12, 21, 1) 100%);
  }

</style>
