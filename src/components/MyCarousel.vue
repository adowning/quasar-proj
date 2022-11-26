<template>
  <!-- <div class="text-h5 text-color-white q-mb-xs">{{ category }}</div> -->
  <!-- <div class="row no-wrap items-center q-mb-sm">
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
  <!-- <div
    style="
      background-image: url(/background/select-bg.png);
      background-size: cover;
      right: 120px;
      padding: 70px;
      height: 100vh;
      width: 700px;
      top: 0px;
      padding-right: 180px;
      /* height: 400px;
        width: 600px; */
      /* position: fixed;
        top: 20; */
    "
  > -->

  <div
    v-if="slides !== undefined"
    style="margin-top: 100px; margin-left: 100px"
  >
    <div v-if="slides.length > 0">
      <Carousel
        :settings="settings"
        ref="myCarousel"
        v-model="currentSlide"
        style="width: 80vw; height: 320px; right: 20px; top: 0px"
        class="q-pa-none q-ma-none"
      >
        <Slide
          v-for="i in slides.length - 1"
          :key="i"
          class="q-pa-none q-ma-none"
        >
          <!-- <div
              v-if="i < slides.length"
              :class="` ${
                slides[i].isHovering
                  ? 'carousel__item dimmed'
                  : 'carousel__item'
              }`"
              @mouseenter="slides[i].isHovering = true"
              @mouseleave="slides[i].isHovering = false"
            > -->
          <!-- <div style="width: 230px; height: 200px"> -->
          <!-- <div
                class="ui panel"
                :class="` ${
                  slides[i].isHovering
                    ? 'carousel__item dimmed'
                    : 'carousel__item'
                }`"
                @mouseenter="slides[i].isHovering = true"
                @mouseleave="slides[i].isHovering = false"
              >
                <div class="ui panel content">
                  <img :src="`/games/${slides[i].name}.jpg`" class="fit" />
                </div>
              </div> -->
          <SciCard :name="slides[i].name" />
          <!-- </div> -->
          <!-- </div> -->
          <!-- <div
              v-if="i < slides.length - 1 && slides[i].isHovering"
              class="carousel__item dimmed"
              @mouseenter="slides[i].isHovering = true"
              @mouseleave="slides[i].isHovering = false"
            >
              <img
                :src="`/games/${slides[i].name}.jpg`"
                class="carousel__item_img dimmed"
              />
            </div> -->
          <!-- <q-btn
                  outline
                  round
                  color="deep-orange"
                  style="top: 0; left: 0"
                  icon="play_arrow"
                /> -->
          <!-- <div
              v-if="i >= slides.length - 1"
              class="carousel__item transparent"
              transparent
            /> -->
          <!-- <q-card class="my-card transparent" transparent> </q-card> -->
        </Slide>

        <template #addons>
          <Navigation />
        </template>
      </Carousel>
    </div>
    <!-- </div> -->
  </div>
</template>

<style lang="scss">
@import url(https://fonts.googleapis.com/css?family=Titillium+Web:400,300,300italic,700italic,700);
body {
  background: black;
  font-family: 'Titillium Web';
}

.ui.panel {
  width: calc(100%-20px);
  height: calc(100%-20px);
  padding: 2px;
  background: #00a1ed; /* fallback */
  background: linear-gradient(0deg, transparent 0px, #00a1ed 0) top left,
    linear-gradient(0deg, transparent 0px, #00a1ed 0) top right,
    linear-gradient(315deg, transparent 10px, #00a1ed 0) bottom right,
    linear-gradient(0deg, transparent 0px, #00a1ed 0) bottom left;
  background-size: 50% 50%;
  background-repeat: no-repeat;
  display: inline-block;
  -webkit-filter: drop-shadow(5px 5px 5px rgba(0, 161, 237, 0.25));
  filter: drop-shadow(5px 5px 5px rgba(0, 161, 237, 0.25));
  width: 100%;
  height: 100%;
}

.ui.panel > .content {
  width: calc(100% - 1em);
  height: calc(100% - 1em);
  padding: 0.3 em;
  color: #00a1ed;
  background: #00202f; /* fallback */
  background: linear-gradient(0deg, transparent 0px, rgba(0, 0, 0, 0.8) 0) top
      left,
    linear-gradient(0deg, transparent 0px, rgba(0, 0, 0, 0.8) 0) top right,
    linear-gradient(315deg, transparent 10px, rgba(0, 0, 0, 0.8) 0) bottom right,
    linear-gradient(0deg, transparent 0px, rgba(0, 0, 0, 0.8) 0) bottom left;
  background-size: 50% 50%;
  background-repeat: no-repeat;
  display: inline-block;
}
.carousel__icon {
  width: var(--vc-icn-width);
  height: var(--vc-icn-width);
  fill: white;
}
.carousel__next {
  box-sizing: content-box;
  background: var(--vc-nav-background);
  border-radius: var(--vc-nav-border-radius);
  width: var(--vc-nav-width);
  height: var(--vc-nav-height);
  text-align: center;
  font-size: var(--vc-nav-height);
  padding: 0;
  color: var(--vc-nav-color);
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  border: 0;
  cursor: pointer;
  margin: 0 -30px;
  top: 50%;
  transform: translateY(-50%);
}
.carousel__prev {
  box-sizing: content-box;
  background: var(--vc-nav-background);
  border-radius: var(--vc-nav-border-radius);
  width: var(--vc-nav-width);
  height: var(--vc-nav-height);
  text-align: center;
  font-size: var(--vc-nav-height);
  padding: 0;
  color: var(--vc-nav-color);
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  border: 0;
  cursor: pointer;
  margin: 0 -30px;
  top: 50%;
  transform: translateY(-50%);
}
.my-card {
  width: 100%;
  height: 100%;
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
.q-card {
  border-style: solid;
  border-radius: 23px;
  border-width: 2px;
  border-color: white;
  height: 100%;
  width: 100%;
  padding: 0px;
}
.carousel__item {
  // border: solid;
  // border-color: transparent;
  height: 127px;
  width: 220px;
  // border-image: url(/icons/card.png) 27 23 / 20px 30px / 1rem round space;

  // border-radius: 23px;
  margin: 0px;
  padding: 0px;
}
.carousel__item_img {
  // border-radius: 23px;
  // height: 127px;
  // border-width: 2px;
  // width: 220px;
  height: 127px;
  width: 220px;
  margin: 0px;
  padding: 0px;
}
.carousel__slide {
  // border-radius: 23px;
  // height: 200px;
  // border-image: url(/icons/top-border.webp) 30% stretch;
  // height: 127px;
  // width: 220px;
  margin: 0px;
  padding: 0px;
}
// .hover_overlay {
//   border-radius: 23px;
//   min-height: 100%;
//   min-width: 100%;
//   z-index: 999;
// }
</style>
<script setup lang="ts">
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel';
import SciCard from './SciCard.vue';
import 'vue3-carousel/dist/carousel.css';

import { ref, onMounted, watch, computed } from 'vue';
// import { Game } from '@/boot/axios';
const myCarousel = ref(null);
const myProgress = 0;
const plabel = ref(0);
const slides = ref();
const hover = ref(false);
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
function getProgress() {
  if (myCarousel.value !== null) {
    myCarousel.value.data.length / myCarousel.value.data.currentSlide;
  }
}
watch(currentSlide, async (currentData, newData) => {
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
  itemsToShow: 3,
  snapAlign: 'center',
};
function next() {
  currentSlide.value = currentSlide.value + 1;
}
function prev() {
  if (currentSlide.value <= 0) return;
  currentSlide.value = currentSlide.value - 1;
}
function setHovering(game: any, b: boolean) {
  game.isHovering = b;
}
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
