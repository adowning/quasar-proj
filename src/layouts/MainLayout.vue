<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="transparent q-ma-none q-pa-none" style="height: 30px">
      <q-toolbar class="q-ma-none q-pa-none q-pl-md" style="height: 30px">
        <!-- <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        /> -->
        <!-- <div class="grid"></div> -->
        <!-- <div class="lines"></div> -->
        <h1>
          <span>PLAYER</span>
          <span>PLAYER</span>
        </h1>
        <h2>edge</h2>

        <q-toolbar-title> </q-toolbar-title>

        <div></div>
      </q-toolbar>
    </q-header>
    <!--
      <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        bordered
      >
        <q-list>
          <q-item-label
            header
          >
            Essential Links
          </q-item-label>

          <EssentialLink
            v-for="link in essentialLinks"
            :key="link.title"
            v-bind="link"
          />
        </q-list>
      </q-drawer> -->

    <!-- <q-page-container
      class=""
      style="
        background-repeat: no-repeat;
        background-size: cover;
        /* opacity: 0.75; */
        background-image: url(/background/sub_header_bg_tablet_landscape.png);
      "
    > -->
    <q-page-container
      class=""
      style="
        background-color: #12202d;
        /* background-image: url(/icons/asdf.png);
        background-repeat: no-repeat;
        background-size: contain; */
      "
    >
      <router-view />
    </q-page-container>
  </q-layout>
</template>
<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Mr+Dafoe&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Exo:wght@900&display=swap');

body,
html {
  width: 100%;
  height: 100%;
  margin: 0;
  overflow: hidden;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  background: radial-gradient(rgba(#7600bf, 0.5) 0%, transparent 70%),
    linear-gradient(#0b161e 40%, #202076 70%);
  perspective: 700px;
  font-size: clamp(10px, 2vw, 20px);
}

.lines {
  $color: #59c1fe;
  position: fixed;
  top: 0;
  width: 100vw;
  height: 3em;
  background: linear-gradient(
    rgba($color, 0.2) 20%,
    $color 40%,
    $color 60%,
    rgba($color, 0.2) 80%
  );
  background-size: 1px 0.5em;
  box-shadow: 0 0 1em rgba($color, 0.4);
  transform: translateY(-1em);
  left: 0;
}

h1 {
  position: relative;
  top: 0;
  font-family: 'Exo';
  font-size: 3em;
  margin: 0;
  transform: skew(-15deg);
  letter-spacing: 0.03em;

  &::after {
    content: '';
    position: absolute;
    top: -0.4em;
    right: 0.05em;
    width: 0.4em;
    height: 0.4em;
    background: radial-gradient(
        white 3%,
        rgba(white, 0.3) 15%,
        rgba(white, 0.05) 60%,
        transparent 80%
      ),
      radial-gradient(rgba(white, 0.2) 50%, transparent 60%) 50% 50% / 5% 100%,
      radial-gradient(rgba(white, 0.2) 50%, transparent 60%) 50% 50% / 70% 5%;
    background-repeat: no-repeat;
  }

  span:first-child {
    display: block;
    text-shadow: 0 0 0.1em #8ba2d0, 0 0 0.2em black, 0 0 5em #165ff3;
    -webkit-text-stroke: 0.06em rgba(black, 0.5);
  }

  span:last-child {
    position: absolute;
    left: 0;
    top: 0;
    background-image: linear-gradient(
      #032d50 25%,
      #00a1ef 35%,
      white 50%,
      #20125f 50%,
      #8313e7 55%,
      #ff61af 75%
    );
    -webkit-text-stroke: 0.01em #94a0b9;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
}

h2 {
  font-family: 'Mr Dafoe';
  // margin: 10;
  left: -20;
  margin-left: -20;
  font-size: 2.5em;
  margin-top: 1em;
  color: white;
  text-shadow: 0 0 0.05em #fff, 0 0 0.2em #fe05e1, 0 0 0.3em #fe05e1;
  transform: rotate(-7deg);
}

.grid {
  $main: #7d41e6;
  $glow: rgba(#2e26ff, 0.4);
  background: linear-gradient(
      transparent 65%,
      $glow 75%,
      $main 80%,
      $glow 85%,
      transparent 95%
    ),
    linear-gradient(
      90deg,
      transparent 65%,
      $glow 75%,
      $main 80%,
      $glow 85%,
      transparent 95%
    );
  background-size: 30px 30px;
  width: 200vw;
  height: 300vh;
  position: absolute;
  bottom: -120vh;
  transform: rotateX(-100deg);
  -webkit-mask-image: linear-gradient(rgba(0, 0, 0, 1), rgba(0, 0, 0, 0) 80%);
}
</style>
<script setup lang="ts">
import { ref } from 'vue';

// import EssentialLink, { EssentialLinkProps } from 'components/EssentialLink.vue';

// const essentialLinks: EssentialLinkProps[] = [
//   {
//     title: 'Docs',
//     caption: 'quasar.dev',
//     icon: 'school',
//     link: 'https://quasar.dev'
//   },
//   {
//     title: 'Github',
//     caption: 'github.com/quasarframework',
//     icon: 'code',
//     link: 'https://github.com/quasarframework'
//   },
//   {
//     title: 'Discord Chat Channel',
//     caption: 'chat.quasar.dev',
//     icon: 'chat',
//     link: 'https://chat.quasar.dev'
//   },
//   {
//     title: 'Forum',
//     caption: 'forum.quasar.dev',
//     icon: 'record_voice_over',
//     link: 'https://forum.quasar.dev'
//   },
//   {
//     title: 'Twitter',
//     caption: '@quasarframework',
//     icon: 'rss_feed',
//     link: 'https://twitter.quasar.dev'
//   },
//   {
//     title: 'Facebook',
//     caption: '@QuasarFramework',
//     icon: 'public',
//     link: 'https://facebook.quasar.dev'
//   },
//   {
//     title: 'Quasar Awesome',
//     caption: 'Community Quasar projects',
//     icon: 'favorite',
//     link: 'https://awesome.quasar.dev'
//   }
// ];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
