<template>
  <q-page
    class="row justify-end items-center q-pa-none q-ma-none q-mr-lg"
    style="
      /* background-image: url(/icons/big-back-skinny.png);
      background-repeat: no-repeat;
      background-size: cover; */
    "
  >
    <div
      class="column q-pa-none q-ma-none q-mr-lg"
      style="height: 100vh; width: 66vw"
    >
      <div v-if="newGames != undefined && popularGames">
        <MyCarousel
          v-if="newGames.length > 0"
          category="New"
          :games="newGames"
        />

        <!-- <MyCarousel category="Popular" :games="popularGames" /> -->
      </div>
    </div>
  </q-page>
</template>
<style lang="scss" scoped>
// body,
// html {
//   width: 100%;
//   height: 100%;
//   margin: 0;
//   overflow: hidden;
// }
</style>
<script setup lang="ts">
import MyCarousel from 'components/MyCarousel.vue';
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
