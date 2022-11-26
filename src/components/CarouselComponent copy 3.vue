<template>
  <!-- <div class="q-pa-md"> -->
  <div v-if="slides">
    <q-carousel
      v-model="slide"
      transition-prev="slide-right"
      transition-next="slide-left"
      swipeable
      animated
      padding
      ref="carousel"
      arrows
      control-color="white"
      control-type="outline"
      height="240px"
      class="q-pa-xs q-ma-sm"
    >
      <!-- <q-carousel-slide
      :name="1"
      img-src="https://cdn.quasar.dev/img/mountains.jpg"
    />
    <q-carousel-slide
      :name="2"
      img-src="https://cdn.quasar.dev/img/parallax1.jpg"
    />
    <q-carousel-slide
      :name="3"
      img-src="https://cdn.quasar.dev/img/parallax2.jpg"
    />
    <q-carousel-slide
      :name="4"
      img-src="https://cdn.quasar.dev/img/quasar.jpg"
    /> -->
      <q-carousel-slide
        :name="1"
        class="row fit no-wrap bg-transparent q-px-lg q-ma-none"
        v-for="slide of Math.floor(slides.length / 3)"
        v-bind:key="slide"
      >
        <!-- <div
        class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap"
      > -->
        <q-img
          class="rounded-borders col-4 full-height q-px-lg"
          :src="`/games/${slides[slide * 3].name}.jpg`"
        />
        {{ Math.floor(slides.length / 3) }}
        {{ slide }}
        <q-img
          class="rounded-borders full-height"
          :src="`/games/${slides[slide * 3 + 1].name}.jpg`"
        />
        <q-img
          class="rounded-borders full-height"
          :src="`/games/${slides[slide * 3 + 2].name}.jpg`"
        />
        <!-- </div> -->
      </q-carousel-slide>

      <!-- <div
        class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap"
      >
        <q-img
          class="rounded-borders col-4 full-height"
          src="https://cdn.quasar.dev/img/mountains.jpg"
        />
        <q-img
          class="rounded-borders col-4 full-height"
          src="https://cdn.quasar.dev/img/parallax1.jpg"
        />
        <q-img
          class="rounded-borders col-4 full-height"
          src="https://cdn.quasar.dev/img/parallax1.jpg"
        />
      </div>
    </q-carousel-slide>
    <q-carousel-slide :name="2" class="column no-wrap">
      <div
        class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap"
      >
        <q-img
          class="rounded-borders col-6 full-height"
          src="https://cdn.quasar.dev/img/parallax2.jpg"
        />
        <q-img
          class="rounded-borders col-6 full-height"
          src="https://cdn.quasar.dev/img/quasar.jpg"
        />
      </div>
    </q-carousel-slide>
    <q-carousel-slide :name="3" class="column no-wrap">
      <div
        class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap"
      >
        <q-img
          class="rounded-borders col-6 full-height"
          src="https://cdn.quasar.dev/img/cat.jpg"
        />
        <q-img
          class="rounded-borders col-6 full-height"
          src="https://cdn.quasar.dev/img/linux-avatar.png"
        />
      </div>
    </q-carousel-slide>-->
      <!-- <q-carousel-slide :name="4" class="column no-wrap">
      <div
        class="row fit justify-start items-center q-gutter-xs q-col-gutter no-wrap"
      >
        <q-img
          class="rounded-borders col-6 full-height"
          src="https://cdn.quasar.dev/img/material.png"
        />
        <q-img
          class="rounded-borders col-6 full-height"
          src="https://cdn.quasar.dev/img/donuts.png"
        />
      </div>
    </q-carousel-slide> -->
      <template v-slot:control>
        <q-carousel-control
          position="left"
          :offset="[10, 80]"
          class="q-gutter-xs"
        >
          <q-btn
            push
            round
            dense
            color="orange"
            text-color="black"
            icon="arrow_left"
            @click="$refs.carousel.previous()"
          />
        </q-carousel-control>
        <q-carousel-control
          position="right"
          :offset="[-10, 80]"
          class="q-gutter-xs"
        >
          <q-btn
            push
            round
            dense
            color="orange"
            text-color="black"
            icon="arrow_right"
            @click="$refs.carousel.next()"
          />
        </q-carousel-control>
      </template>
    </q-carousel>
  </div>
  <!-- </div> -->
</template>
<style scoped lang="scss">
.q-panel {
  background-color: hsl(0, 0%, 0%, 0) !important;
}
.q-carousel {
  background-color: hsl(0, 0%, 0%, 0) !important;
}
</style>
<script setup>
import { ref, onMounted } from 'vue';
const carousel = ref(null);
const slides = ref();
const slide = ref(1);
var xslide = ref(1);

const props = defineProps({
  games: {
    type: Array,
    required: true,
  },
  category: {
    type: String,
  },
});
onMounted(async () => {
  if (props.games.length > 0) {
    // slides.value = props.games;
    // let x = 0;
    // let i = 0;
    // let a = [];
    // let b = [];
    // props.games.forEach((item) => {
    //   // var result = (n - Math.floor(n)) !== 0;
    //   i++;
    //   var n = i / 3;
    //   if (!(n - Math.floor(n) !== 0)) {
    //     b.push(a);
    //     a = [];
    //     x++;
    //   }
    //   a.push(item);
    // });
    // slides.value = b;
    // xslide.value = slides.value.length;
    slides.value = props.games;
  }
  console.log(slides.value.length);
});
</script>
