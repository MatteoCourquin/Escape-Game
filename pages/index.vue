<template>
  <div>
    <TheHeader :pays=pays />
    <Hero />
    <Parallax :pays=pays />
  </div>
</template>

<script>

import TheHeader from '../components/TheHeader.vue';
import Hero from '../components/Hero.vue';
import Parallax from '../components/Parallax.vue';

export default {
  name: "IndexPage",
  components: { TheHeader, Hero, Parallax },
  data() {
    return {
      pays: [
        {
          name: "Comcity",
          path: 'us',
        },
        {
          name: "3DLand",
          path: 'india',
        },
        {
          name: "Creaworld",
          path: 'egypt',
        },
        {
          name: "Japon",
          path: 'japan',
        },
        {
          name: "Russie",
          path: 'russia',
        },
      ]
    };
  },
}
</script>

<style lang="scss">

@import "~/static/scss/main.scss";

</style>
