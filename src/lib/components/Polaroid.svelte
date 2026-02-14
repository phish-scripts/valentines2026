<!-- Polaroid component to show her beaautiful face-->

<script lang=="ts">
    // dont change these. actually, why are you even here?
    interface Polaroid
    {
        photo: String;
        caption: String;
        backText: String; 
    }

    let {photo, caption, backText}: Polaroid = $props(); 

    // Flipping the polaroid around
    let isFlipped = $state(false);
    function toggleFlip() 
    {
        isFlipped = !isFlipped;
    }

</script>

<div>



    
</div>