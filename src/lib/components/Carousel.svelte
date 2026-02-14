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
			class="btn btn-circle glass text-indigo-900 pointer-events-auto shadow-lg hover:scale-110 transition-transform border-none bg-white/50 backdrop-blur-sm"
		>
			❮
		</button>

		<button
			onclick={next}
			class="btn btn-circle glass text-indigo-900 pointer-events-auto shadow-lg hover:scale-110 transition-transform border-none bg-white/50 backdrop-blur-sm"
		>
			❯
		</button>
	</div>

	<div class="flex justify-center items-center gap-3 mt-6">
		{#each memories as _, i}
			<button
				onclick={() => scrollToIndex(i)}
				aria-label="Go to slide {i + 1}"
				class="transition-all duration-300 ease-out shadow-sm rounded-sm
          {currentIndex === i
					? 'w-4 h-4 bg-indigo-600 scale-125 shadow-indigo-500/50 rotate-3' 
					: 'w-3 h-3 bg-gray-300 hover:bg-indigo-300 hover:scale-110 -rotate-3'}"
			></button>
		{/each}
	</div>

</div>