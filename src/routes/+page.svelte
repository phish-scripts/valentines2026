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
      backText: "I love the way you are looking at me. I could look at you forever"
    },
    {
      image: "/photos/evaBarnesAndNoble1.png",
      caption: "\"Bookshelves\"",
      backText: "I love the way your hair falls on your shoulders. It is the silkiest."
    },
    {
      image: "/photos/evaBarnesAndNobleAlt.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/evaBarnesAndNobleAlt4.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/evaBarnesAndNobleAlt5.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/evaCar4.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/evaKpot4.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/evaPrincesTeaHouse.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/evaSubway.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/happyBirthdayEva3.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/polaraoid5.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/polaraoid2.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/polaraoid3.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/polaraoid4.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/polaraoid6.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },
    {
      image: "/photos/polaraoid7.png",
      caption: "Morning Brew",
      backText: "I still remember your order: Iced Oat Latte, two pumps of vanilla."
    },

    // Add as many as you want...
  ];
</script>

<div class="min-h-screen bg-neutral-50 flex flex-col items-center justify-center p-4">
  <h1 class="text-4xl font-bold text-gray-800 mb-8 font-serif italic">To: Eva</h1>
  
  <Carousel {memories} />
  
  <p class="mt-8 text-sm text-gray-400">Click a card to read the memory</p>
</div>