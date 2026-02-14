<!-- Polaroid component to show her beaautiful face-->

<script lang="ts">
    // dont change these. actually, why are you even here?
    interface Polaroid {
        photo: string;
        backText: string; 
    }

    let { photo, backText }: Polaroid = $props();

    // Flipping the polaroid around
    let isFlipped = $state(false);
    function toggleFlip() 
    {
        isFlipped = !isFlipped;
    }

</script>


<div 
  class="group my-12 mx-auto cursor-pointer w-72 aspect-[3/4] [perspective:1000px]"
  onclick={toggleFlip}
  role="presentation"
>
  <div 
    class="relative w-full h-full duration-700 [transform-style:preserve-3d] transition-all ease-in-out border border-gray-200 bg-white shadow-xl"
    class:is-flipped={isFlipped}
  >
    
    <div class="absolute inset-0 p-4 pb-16 bg-white flex flex-col [backface-visibility:hidden]">
      <div class="aspect-square w-full bg-gray-50 overflow-hidden border border-gray-100">
        <img src={photo} alt="" class="w-full h-full object-cover" />
      </div>
      <div class="flex-grow flex items-center justify-center">
         <span class="font-serif text-lg italic text-gray-800"></span>
      </div>
    </div>

    <div class="absolute inset-0 p-8 bg-white flex items-center justify-center [transform:rotateY(180deg)] [backface-visibility:hidden]">
       <p class="font-serif text-center italic text-gray-600 leading-relaxed">{backText}</p>
    </div>
  </div>
</div>

<style>
  /* 1. The Hover Tilt 
     We target the inner card directly for the tilt.
     'group-hover' allows the wrapper to trigger the child's movement.
  */
  .group:hover .relative:not(.is-flipped) {
    transform: rotateY(10deg) rotateX(5deg);
    box-shadow: 25px 25px 50px -12px rgba(0, 0, 0, 0.25); /* Deep shadow on lift */
  }

  /* 2. The Flip */
  .is-flipped {
    transform: rotateY(180deg);
    box-shadow: -25px 25px 50px -12px rgba(0, 0, 0, 0.25); /* Reverse shadow when flipped */
  }
</style>