<template>
  <!-- <Carousel :settings="settings" :breakpoints="breakpoints">
    <Slide v-for="slide in 10" :key="slide">
      <div class="carousel__item">
        <q-img
          :src="url"
          spinner-color="white"
          style="height: 140px; max-width: 150px"
        />
      </div>
    </Slide>

    <template #addons>
      <Navigation />
    </template>
  </Carousel> -->
  <!-- <div class="text-h5 text-color-white q-mb-xs">{{ category }}</div>
  <div class="row no-wrap items-center q-mb-sm">
    <q-btn
      outline
      round
      color="white"
      @click="prev"
      icon="arrow_back_ios"
      size="sm"
    />
    <div class="col-2 q-px-sm">
      <q-linear-progress
        class="w-200px"
        stripe
        rounded
        size="14px"
        color="dark-blue"
        :value="percent"
      >
        <div class="absolute-full flex flex-center">
          <q-badge
            color="dark-blue"
            text-color="dark-blue"
            :label="`${plabel + 1}  of ${slides?.length}`"
          />
        </div>
      </q-linear-progress>
    </div>
    <q-btn
      outline
      round
      color="white"
      @click="next"
      icon="arrow_forward_ios"
      size="sm"
    />
  </div> -->
  <!-- <div v-if="slides" class="q-pa-none q-ma-none"> -->
  <!-- <Carousel
      :settings="settings"
      ref="myCarousel"
      :breakpoints="breakpoints"
      v-model="currentSlide"
      class="q-pa-none q-ma-none"
    > -->
  <!-- <Slide v-for="i in slides.length - 1" :key="i" class="q-pa-none"> -->
  <Carousel :settings="settings" :breakpoints="breakpoints">
    <Slide v-for="i in slides" :key="i">
      <div class="carousel__item">{{ slides[i] }}</div>
      <!-- <q-card class="my-card" v-for="i in slides.length - 1" :key="i"> -->
      <!-- {{ slides[i] }} -->
      <div
        v-if="i < slides.length - 1 && !slides[i].isHovering"
        style="width: 240px"
        @mouseenter="slides[i].isHovering = true"
        @mouseleave="slides[i].isHovering = false"
      >
        <img
          :src="`/games/${slides[i].name}.jpg`"
          class=""
          style="width: 240px"
        />
      </div>

      <div
        v-if="i < slides.length - 1 && slides[i].isHovering"
        class="carousel__item dimmed"
        @mouseenter="slides[i].isHovering = true"
        @mouseleave="slides[i].isHovering = false"
      >
        <img
          :src="`/games/${slides[i].name}.jpg`"
          class="carousel__item_img dimmed"
        />
      </div>
      <!-- <q-btn
                  outline
                  round
                  color="deep-orange"
                  style="top: 0; left: 0"
                  icon="play_arrow"
                /> -->
      <div
        v-if="i >= slides.length - 1"
        class="carousel__item transparent"
        transparent
      />
      <!-- <q-card class="my-card transparent" transparent> </q-card> -->
      <!-- </Slide> -->
      <!-- </q-card> -->
    </Slide>
  </Carousel>
  <!-- </div>  -->
</template>
<style lang="scss">
.my-card {
  width: 240px;
  height: 200px;
  box-sizing: border-box;
  cursor: pointer;
  font: inherit;
  border: none;
  box-shadow: none;
  background: transparent;
  --webkit-appearance: none;
  position: absolute;
  width: 89px;
  top: 50%;
  left: 50%;
  z-index: 1;
  padding: 0;
  transform: translate(-50%, -50%);
  opacity: 0;
  transition: 0.2s linear;
}
// .q-card {
//   border-style: solid;
//   border-radius: 23px;
//   border-width: 2px;
//   border-color: white;
//   height: 100%;
//   width: 100%;
//   padding: 0px;
// }
.carousel__item {
  border-width: 2px;
  height: 200px;
  width: 240px;
  border-radius: 23px;
}
.carousel__item_img {
  border-radius: 23px;
  height: 200px;
  width: 285px;
}
// .hover_overlay {
//   border-radius: 23px;
//   min-height: 100%;
//   min-width: 100%;
//   z-index: 999;
// }
</style>
<script setup lang="ts">
import { Carousel, Slide } from 'vue3-carousel';

import 'vue3-carousel/dist/carousel.css';

import { ref, onMounted, watch } from 'vue';
// import { Game } from '@/boot/axios';
// const myCarousel = ref(null);
const plabel = ref(0);
const slides = ref();
const currentSlide = ref(0);
const percent = ref(0);
const props = defineProps({
  games: {
    type: Array,
    required: true,
  },
  category: {
    type: String,
  },
});
// if (myCarousel.data.currentSlide === 10) {
//   // Do your magic here

// }
// const plabel = computed(() => ((
//       myCarousel?.value?.data.length / myCarousel?.value?.data.currentSlide
//     ).toFixed(2) + '%'))
watch(currentSlide, async () => {
  console.log('asdf');
  percent.value = currentSlide.value / slides.value.length;
  plabel.value = percent.value * 10;
});
onMounted(async () => {
  if (props.games.length > 0) {
    slides.value = props.games;
  }
});
const settings = {
  itemsToShow: 1,
  // snapAlign: 'center',
};
// function next() {
//   currentSlide.value = currentSlide.value + 1;
// }
// function prev() {
//   if (currentSlide.value <= 0) return;
//   currentSlide.value = currentSlide.value - 1;
// }

const breakpoints = {
  // 700px and up
  300: {
    itemsToShow: 1,
    snapAlign: 'center',
  },
  500: {
    itemsToShow: 2,
    snapAlign: 'center',
  },
  725: {
    itemsToShow: 3.5,
    snapAlign: 'center',
  },
  1000: {
    itemsToShow: 4,
    snapAlign: 'center',
  },
  // 1024 and up
  1100: {
    itemsToShow: 4.5,
    snapAlign: 'start',
  },
  1324: {
    itemsToShow: 4.5,
    snapAlign: 'start',
  },
};
</script>
