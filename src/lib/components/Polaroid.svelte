<script lang="ts">
	import { spring } from 'svelte/motion';

	let { image, caption, backText } = $props<{
		image: string;
		caption: string;
		backText: string;
	}>();

	let isFlipped = $state(false);

	const tilt = spring({ x: 0, y: 0 }, { stiffness: 0.1, damping: 0.4 });

	function handleMouseMove(e: MouseEvent) {
		const card = e.currentTarget as HTMLElement;
		const { width, height, left, top } = card.getBoundingClientRect();
		const x = (e.clientX - left) / width - 0.5;
		const y = (e.clientY - top) / height - 0.5;
		tilt.set({ x: x * 20, y: y * -20 });
	}

	function resetTilt() {
		tilt.set({ x: 0, y: 0 });
	}
</script>

<div
	class="group perspective-1000 my-12 mx-auto cursor-pointer w-72 h-96 relative"
	onmousemove={handleMouseMove}
	onmouseleave={resetTilt}
	onclick={() => (isFlipped = !isFlipped)}
	role="presentation"
>
	<div
		class="relative w-full h-full duration-500 preserve-3d transition-transform ease-out"
		style:transform={`rotateY(${isFlipped ? 180 : 0}deg) rotateY(${$tilt.x}deg) rotateX(${$tilt.y}deg)`}
	>
		<div
			class="absolute -right-4 -bottom-4 w-full h-full bg-indigo-600 rounded-sm -z-10 transform -rotate-2 outline-[1px] outline-transparent translate-z-0"
		></div>

		<div 
      class="relative w-full h-full preserve-3d shadow-[0_0_0_2px_#111827] bg-amber-50"
    >
			
			<div 
        class="absolute inset-0 bg-amber-50 flex flex-col p-4 pb-16 outline-[1px] outline-transparent"
        style="backface-visibility: hidden; -webkit-backface-visibility: hidden;"
      >
				<div
					class="absolute inset-0 opacity-20 pointer-events-none z-50"
					style="background-image: url('data:image/svg+xml,%3Csvg viewBox=%220 0 200 200%22 xmlns=%22http://www.w3.org/2000/svg%22%3E%3Cfilter id=%22noiseFilter%22%3E%3CfeTurbulence type=%22fractalNoise%22 baseFrequency=%220.65%22 numOctaves=%223%22 stitchTiles=%22stitch%22/%3E%3C/filter%3E%3Crect width=%22100%25%22 height=%22100%25%22 filter=%22url(%23noiseFilter)%22 opacity=%221%22/%3E%3C/svg%3E');"
				></div>

        <div class="aspect-square w-full bg-indigo-200 overflow-hidden relative shadow-[0_0_0_2px_#111827]">
					<img
						src={image}
						alt={caption}
						class="w-full h-full object-cover grayscale-[20%] sepia-[30%] contrast-125"
					/>
				</div>
				<div class="flex-grow flex items-center justify-center">
					<span
						class="font-serif text-xl italic font-bold text-gray-900 tracking-tighter"
						style="font-family: 'Courier New', monospace;">{caption}</span
					>
				</div>
			</div>

			<div
				class="absolute inset-0 bg-amber-50 flex items-center justify-center p-8 outline-[1px] outline-transparent"
        style="transform: rotateY(180deg); backface-visibility: hidden; -webkit-backface-visibility: hidden;"
			>
				<div
					class="absolute inset-0 opacity-20 pointer-events-none z-50"
					style="background-image: url('data:image/svg+xml,%3Csvg viewBox=%220 0 200 200%22 xmlns=%22http://www.w3.org/2000/svg%22%3E%3Cfilter id=%22noiseFilter%22%3E%3CfeTurbulence type=%22fractalNoise%22 baseFrequency=%220.65%22 numOctaves=%223%22 stitchTiles=%22stitch%22/%3E%3C/filter%3E%3Crect width=%22100%25%22 height=%22100%25%22 filter=%22url(%23noiseFilter)%22 opacity=%221%22/%3E%3C/svg%3E');"
				></div>

        <div class="border-2 border-dashed border-gray-300 p-6 w-full h-full flex items-center justify-center">
					<p class="font-mono text-center text-sm font-bold text-indigo-900 leading-relaxed">
						{backText}
					</p>
				</div>
			</div>

		</div>
	</div>
</div>

<style>
	.perspective-1000 {
		perspective: 1000px;
	}
	.preserve-3d {
		transform-style: preserve-3d;
	}
  /* Force hardware acceleration for smoother edges */
  .translate-z-0 {
    transform: translateZ(0);
  }
</style>