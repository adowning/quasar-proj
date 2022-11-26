<template>
  <q-page class="row justify-end items-center q-pa-none q-ma-none q-mr-lg">
    <div
      class="column q-pa-none q-ma-none q-mr-lg"
      style="height: 700px; width: 66%"
    >
      <!-- <div class="col-1 q-pa-none q-ma-none"></div> -->
      <!-- <q-card class="transparent no-shadow q-pa-none q-ma-none q-mx-xl">
        <q-card-section class="q-pa-none q-ma-none"> -->
      <div :v-if="newGames != null">
        <carousel-component
          :games="newGames"
          class="col q-pa-none q-ma-none"
        ></carousel-component>
      </div>

      <!-- </q-card-section>
      </q-card> -->
      <q-card class="transparent no-shadow q-pa-none q-ma-none q-mx-xl">
        <q-card-section class="q-pa-none q-ma-none">
          <carousel-component
            v-if="newGames && popularGames"
            :games="popularGames!"
            class="col q-pa-none q-ma-none"
          ></carousel-component>
        </q-card-section>
      </q-card>
      <div class="col-1 q-pa-none q-ma-none"></div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import CarouselComponent from 'components/CarouselComponent.vue';
import { Game } from 'src/types';
import axios from 'axios';
import { onMounted, ref } from 'vue';
const games = ref();
const newGames = ref<Game[] | null>(null);
const popularGames = ref<Game[] | null>(null);
onMounted(async () => {
  const { data } = await axios.get('/worker/initial/0');
  const xgames = data;
  console.log(games);
  if (xgames !== null) {
    newGames.value = xgames.newGames;
    popularGames.value = xgames.popularGames;
    // console.log(popularGames.value.length);
  }
});
</script>
