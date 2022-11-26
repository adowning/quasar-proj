<script setup lang="ts">
import { ref } from 'vue';

const slide = ref(1);
const autoplay = ref(true);
</script>
<template>
  <div class="q-pa-md">
    <q-carousel swipeable animated v-model="slide" ref="carousel" infinite>
      <!-- <q-responsive :ratio="16 / 9"> -->
      <q-carousel-slide
        :name="1"
        img-src="/games/Africa.jpg"
        style="width: 140px; max-height: 140px"
      />
      <!-- <q-responsive :ratio="16 / 9"> -->
      <q-carousel-slide
        :name="2"
        img-src="/games/Africa.jpg"
        style="width: 140px; max-height: 140px"
      />
      <!-- </q-responsive> -->
      <!-- <q-responsive :ratio="16 / 9"> -->
      <q-carousel-slide
        :name="3"
        img-src="/games/Africa.jpg"
        style="width: 140px; max-height: 140px"
      />
      <!-- </q-responsive> -->
      <!-- <q-responsive :ratio="16 / 9"> -->
      <q-carousel-slide
        :name="4"
        img-src="/games/Africa.jpg"
        style="width: 140px; max-height: 140px"
      />

      <!-- </q-responsive> -->

      <template v-slot:control>
        <q-carousel-control
          position="top-right"
          :offset="[18, 18]"
          class="text-white rounded-borders"
          style="background: rgba(0, 0, 0, 0.3); padding: 4px 8px"
        >
          <q-toggle
            dense
            dark
            color="orange"
            v-model="autoplay"
            label="Auto Play"
          />
        </q-carousel-control>

        <q-carousel-control
          position="bottom-right"
          :offset="[18, 18]"
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
</template>
