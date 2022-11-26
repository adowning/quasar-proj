<script setup lang="ts">
defineProps({
  // title: {
  //   type: String,
  // },
  name: {
    type: String,
    required: true,
  },
});
</script>
<template>
  <!-- <div class="scicardimg">
    <img
      :src="`/games/${name}.jpg`"
      style="
        width: 220px;
        height: 200px;
        top: 0px;
        left: 0px;
        position: absolute;
      "
    /> -->
  <div class="boxcontainer">
    <div class="scicard">
      <img
        :src="`/games/FishHunterKA.jpg`"
        style="
          width: 260px;
          height: 180px;
          top: 20px;
          left: 0px;
          position: absolute;
        "
      />
      <div class="overlay">
        <img :src="`/icons/game-back.png`" style="position: absolute" />
      </div>
    </div>
  </div>

  <!-- </div> -->
</template>
<style lang="scss">
.boxcontainer {
  margin: 0px;
  padding: 0px;
  margin-bottom: 40px;
  width: 260px;
  height: 243px;
  overflow: visible;
  background-color: transparent;
}
.scicard {
  margin: 0px;
  padding: 0px;
  width: 260px;
  height: 243px;
  top: 50px;
  left: 0px;
  position: absolute;
  overflow: visible;

  // width: 260px;
  // padding: 0px;
  // height: 223px;
  // z-index: 25;
  // margin: 0px;
  // background-size: cover;
  // background-repeat: no-repeat;

  // position: absolute;
}
.overlay {
  top: 0px;
  margin: 0px;
  padding: 0px;
  left: -10px;
  position: absolute;
  overflow: visible;
}
// .scicardimg {
// max-width: 250px;
// max-height: 210px;
// z-index: 5;
// }
// .border {
//   background-size: cover;
//   background-image: url(/icons/game-back.png);
//   width: 100%;
//   height: 100%;
//   top: -30px;
//   left: -20;
//   position: relative;
//   padding: 0px;
// }
</style>
