<template>
  <!-- {{ slides }} -->
  <!-- <Carousel :settings="settings" :breakpoints="breakpoints">
    <Slide v-for="slide in slides" :key="slide">
      <div class="carousel__item">{{ slides[i] }}</div>
      <div
        v-if="!slide.isHovering"
        style="width: 240px"
        @mouseenter="slide.isHovering = true"
        @mouseleave="slide.isHovering = false"
      >
        <img :src="`/games/${slide.name}.jpg`" class="" style="width: 240px" />
      </div>

      <div
        v-if="slide.isHovering"
        class="carousel__item dimmed"
        @mouseenter="slide.isHovering = true"
        @mouseleave="slide.isHovering = false"
      >
        <img
          :src="`/games/${slide.name}.jpg`"
          class="carousel__item_img dimmed"
        />
      </div>
    </Slide>
  </Carousel> -->
  <template>
    <Carousel>
      <Slide v-for="slide in 10" :key="slide">
        <div class="carousel__item">{{ slide }}</div>
      </Slide>

      <template #addons>
        <Navigation />
        <Pagination />
      </template>
    </Carousel>
  </template>
</template>
<style scoped lang="scss">
.carousel__item {
  min-height: 200px;
  width: 100%;
  background-color: var(--vc-clr-primary);
  color: var(--vc-clr-white);
  font-size: 20px;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.carousel__slide {
  padding: 10px;
}

.carousel__prev,
.carousel__next {
  box-sizing: content-box;
  border: 5px solid white;
}
// .my-card {
//   width: 240px;
//   height: 200px;
//   box-sizing: border-box;
//   cursor: pointer;
//   font: inherit;
//   border: none;
//   box-shadow: none;
//   background: transparent;
//   --webkit-appearance: none;
//   position: absolute;
//   width: 89px;
//   top: 50%;
//   left: 50%;
//   z-index: 1;
//   padding: 0;
//   transform: translate(-50%, -50%);
//   opacity: 0;
//   transition: 0.2s linear;
// }
// .q-card {
//   border-style: solid;
//   border-radius: 23px;
//   border-width: 2px;
//   border-color: white;
//   height: 100%;
//   width: 100%;
//   padding: 0px;
// }
// .carousel__item {
//   border-width: 2px;
//   height: 200px;
//   width: 240px;
//   border-radius: 23px;
// }
// .carousel__item_img {
//   border-radius: 23px;
//   height: 200px;
//   width: 285px;
// }
</style>
<script setup>
import { Carousel, Slide, Navigation, Pagination } from 'vue3-carousel';

import 'vue3-carousel/dist/carousel.css';

// import { ref, onMounted, watch } from 'vue';
// import { Game } from '@/boot/axios';
// const myCarousel = ref(null);
// const plabel = ref(0);
// const slides = ref();
// const currentSlide = ref(0);
// const percent = ref(0);
defineProps({
  games: {
    type: Array,
    required: true,
  },
  category: {
    type: String,
  },
});
// watch(currentSlide, async () => {
//   console.log('asdf');
//   percent.value = currentSlide.value / slides.value.length;
//   plabel.value = percent.value * 10;
// });
// onMounted(async () => {
//   if (props.games.length > 0) {
//     slides.value = props.games;
//   }
// });
// const settings = {
//   itemsToShow: 1,
//   // snapAlign: 'center',
// };
</script>
