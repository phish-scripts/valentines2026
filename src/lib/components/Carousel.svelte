<script lang="ts">
	import Polaroid from './Polaroid.svelte';

	// 1. Types
	type Memory = {
		image: string;
		caption: string;
		backText: string;
	};

	// 2. Props
	let { memories } = $props<{ memories: Memory[] }>();

	// 3. State
	let currentIndex = $state(0);
	let carousel: HTMLDivElement;

	// 4. Smooth Logic
	function scrollToIndex(index: number) {
		if (!carousel) return;
		const width = carousel.offsetWidth;
		carousel.scrollTo({
			left: width * index,
			behavior: 'smooth'
		});
		currentIndex = index;
	}

	function next() {
		const newIndex = (currentIndex + 1) % memories.length;
		scrollToIndex(newIndex);
	}

	function prev() {
		const newIndex = (currentIndex - 1 + memories.length) % memories.length;
		scrollToIndex(newIndex);
	}
</script>

<div class="relative w-full max-w-lg mx-auto flex flex-col items-center">
	
	<div
		bind:this={carousel}
		class="carousel w-full overflow-hidden scroll-smooth relative rounded-box"
		style="scroll-snap-type: x mandatory;" 
	>
		{#each memories as memory, i}
			<div 
        id="slide{i}" 
        class="carousel-item w-full flex justify-center py-4"
        style="scroll-snap-align: start;"
      >
				<Polaroid
					image={memory.image}
					caption={memory.caption}
					backText={memory.backText}
				/>
			</div>
		{/each}
	</div>

	<div
		class="absolute flex justify-between transform -translate-y-1/2 left-0 right-0 top-1/2 pointer-events-none px-4"
	>
		<button
            onclick={prev}
            class="btn btn-square bg-amber-50 border-2 border-black shadow-[4px_4px_0px_0px_rgba(0,0,0,1)] 
            hover:translate-x-[2px] hover:translate-y-[2px] hover:shadow-none 
            transition-all active:bg-indigo-100 pointer-events-auto"
        >
            <span class="text-2xl font-bold text-indigo-900">❮</span>
        </button>

		<button
            onclick={next}
            class="btn btn-square bg-amber-50 border-2 border-black shadow-[4px_4px_0px_0px_rgba(0,0,0,1)] 
            hover:translate-x-[2px] hover:translate-y-[2px] hover:shadow-none 
            transition-all active:bg-indigo-100 pointer-events-auto"
        >
            <span class="text-2xl font-bold">❯</span>
        </button>
	</div>
    

	<div class="flex justify-center items-center gap-3 mt-6">
		{#each memories as _, i}
			<button
				onclick={() => scrollToIndex(i)}
				aria-label="Go to slide {i + 1}"
				class="transition-all duration-300 ease-out shadow-sm rounded-none border border-black
          {currentIndex === i
					? 'w-4 h-4 bg-primary scale-125 rotate-3 shadow-md' 
					: 'w-3 h-3 bg-base-300 hover:bg-secondary hover:scale-110 -rotate-3'}"
			></button>
		{/each}
	</div>

</div>