<script lang="ts">
  import Carousel from '$lib/components/Carousel.svelte';

  // Your Data Array
  const memories = [
    {
      image: "/photos/eva1.png", // Make sure these are in your /static folder
      caption: "\"2nd Hangout\"",
      backText: "This was the first day I started taking pictures of you. From then on I knew I wanted to take pictures of you for the rest of my life."
    },
    {
      image: "/photos/evaBanhMi.png",
      caption: "\"Paris Banh Mi\"",
      backText: "I love the way you are looking at me. I could look at you forever."
    },
    {
      image: "/photos/evaBarnesAndNoble1.png",
      caption: "\"Bookshelves\"",
      backText: "I love the way your hair falls on your shoulders. It is the silkiest."
    },
    {
      image: "/photos/evaBarnesAndNobleAlt.png",
      caption: "\"Matcha\"",
      backText: "Your eyes twinkle like stars; I love looking at them."
    },
    {
      image: "/photos/evaBarnesAndNobleAlt4.png",
      caption: "\"Pose\"",
      backText: "You are so fineeee."
    },
    {
      image: "/photos/evaBarnesAndNobleAlt5.png",
      caption: "\"Reading\"",
      backText: "I didn't expect that reading with you at barnes & noble would change my life. But then again, each experience with you changes my life for the better."
    },
    {
      image: "/photos/evaCar4.png",
      caption: "\";3\"",
      backText: "they big :3"
    },
    {
      image: "/photos/evaKpot4.png",
      caption: "\"KPot Pt.1\"",
      backText: "You look so hot when you eat."
    },
    {
      image: "/photos/evaPrincesTeaHouse.png",
      caption: "\"Prince Tea House\"",
      backText: ""
    },
    {
      image: "/photos/evaSubway.png",
      caption: "\"Subway\"",
      backText: "I loved holding you on the subway."
    },
    {
      image: "/photos/happyBirthdayEva3.png",
      caption: "\"Happy Birthday\"",
      backText: "I feel so special that I got to spend your birthday with you. I want to celebrate your birthday for the rest of my life."
    },
    {
      image: "/photos/polaraoid5.png",
      caption: "\"Boba\"",
      backText: "You look so hot drinking boba. I love the way your eyes look."
    },
    {
      image: "/photos/polaroid2.png",
      caption: "\"Bread\"",
      backText: "lol remember when i spent $8.50 on water"
    },
    {
      image: "/photos/polaroid3.png",
      caption: "\"Cinnamaroll\"",
      backText: "You look so cute. You are the cutest. the cutest EVER"
    },
    {
      image: "/photos/polaroid4.png",
      caption: "\"Car\"",
      backText: ":3"
    },
    {
      image: "/photos/polaroid6.png",
      caption: "\"Foliage\"",
      backText: "I love the way the light hits your face. You look so fine omg"
    },
    {
      image: "/photos/polaroid7.png",
      caption: "\"Cat Jacket\"",
      backText: "woa eva a CAT woa woa :flooshed:"
    }

    // Add as many as you want...
  ];
</script>

<div class="min-h-screen bg-neutral-50 flex flex-col items-center justify-center p-4">
  <h1 class="text-4xl font-bold text-white mb-8 font-serif italic bg-black p-5">To: Eva</h1>
  
  <Carousel {memories} />
  
  <p class="mt-8 text-sm bg-black text-white p-2">Flip to read each memory.</p>
</div>