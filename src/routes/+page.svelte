<script lang="ts">
  import Polaroid from '$lib/components/Polaroid.svelte';
</script>

<main class="min-h-screen flex flex-col items-center justify-center gap-8 p-10">
  <h1 class="text-4xl font-bold text-rose-600 mb-8"></h1>
  
  <Polaroid 
    image="/photos/our-first-date.jpg" 
    caption="sample"
    backText="The day everything changed. I still have the receipt from dinner!"
  />
</main>