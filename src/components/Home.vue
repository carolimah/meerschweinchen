<template>
  <nav class="fixed top-0 right-5 z-50">
    <ul class="flex flex-row">
      <li class="mr-[15px]"><a href="#home">HOME</a></li>
      <li class="mr-[15px]"><a href="#about">ÜBER MICH</a></li>
      <li><a href="#shop">SHOP</a></li>
    </ul>
  </nav>
  <section class="relative" id="home">
    <img
      class="w-full inset-0 object-cover"
      src="../assets/img/gras1.jpg"
      alt=""
    />
    <div class="absolute text-left top-2/3 left-5  -translate-y-2/3">
      <h1>Borsteler-Meeries</h1>
      <h2>Meerschweinchen aus liebevoller Hobbyzucht</h2>
      <button
        class="bg-dark-brown text-beige p-3 border border-beige-100 rounded-full text-[20px] hover:bg-light-brown hover:cursor-pointer"
      >
        Zu den Meeries
      </button>
    </div>
  </section>
  <section id="about" class="w-full flex justify-center">
   
    <div class="bg-green/70 w-2/3 m-10 p-10">
      <h2 class="text-center">Hallo und herzlich willkommen!</h2>
      <br />
      <p>
        Ich bin Ralf und betreibe mit viel Herzblut eine kleine, liebevolle
        Meerschweinchen-Hobbyzucht. Was als Interesse an diesen neugierigen,
        sozialen Tieren begann, ist über die Jahre zu einer echten Leidenschaft
        geworden. Unsere Meerschweinchen wachsen in artgerechter Haltung mit
        viel Platz, frischer Luft und täglicher Zuwendung auf. Vom ersten Tag an
        legen wir großen Wert auf Gesundheit, ein gutes Sozialverhalten und eine
        liebevolle Prägung – damit unsere Tiere später in ihren neuen Familien
        glücklich werden. Auf dieser Seite findest du Informationen zu aktuellen
        Würfen, Abgabetieren und unserem Zubehörshop, den wir mit hochwertigen
        Produkten betreiben, die wir selbst getestet haben und empfehlen können.
        Schau dich gern um – bei Fragen sind wir immer für dich da!
      </p>
      <br />
      <p>Herzliche Grüße <br />Ralf</p>
    </div>
    <div
      ref="container"
      class="relative h-full w-fit  flex flex-col-reverse items-center gap-6"
    >
      <img
        v-for="(img, index) in images"
        :key="index"
        :src="img"
        class="opacity-0 w-12 object-contain"
        :ref="(el) => (imageRefs[index] = el)"
      />
    </div>
  </section>
</template>
<script setup>
import { ref, onMounted } from "vue";
import { gsap } from "gsap";

const images = [
  new URL("../assets/img/print-right.jpg", import.meta.url).href,
  new URL("../assets/img/print-left.jpg", import.meta.url).href,
  new URL("../assets/img/print-right.jpg", import.meta.url).href,
  new URL("../assets/img/print-left.jpg", import.meta.url).href,
];

const imageRefs = [];

onMounted(() => {
  const tl = gsap.timeline({ repeat: -1 });

  imageRefs.forEach((img, i) => {
    tl.fromTo(
      img,
      { opacity: 0 },
      {
        opacity: 1,
        duration: 0.8,
        ease: "power2.inOut",
      },
      i * 0.8 // Verzögerung je Bild
    ).to(
      img,
      { opacity: 0, duration: 0.8, ease: "power2.inOut" },
      i * 0.8 + 0.6 // ein bisschen sichtbar bleiben
    );
  });
});
</script>
