<template>
  <div>
    <TheHeader :pays=pays />
    <Hero />
    <Parallax :pays=pays />
    <TheFooter />
  </div>
</template>

<script>

import TheHeader from '../components/TheHeader.vue';
import Hero from '../components/Hero.vue';
import Parallax from '../components/Parallax.vue';
import TheFooter from '../components/TheFooter.vue';

export default {
  name: "IndexPage",
  components: { TheHeader, Hero, Parallax, TheFooter },
  data() {
    return {
      pays: [
        {
          name: "Comcity",
          path: 'us',
          room: 'au Creativ\'Lab'
        },
        {
          name: "3DLand",
          path: 'india',
          room: 'au Hub'
        },
        {
          name: "Creaworld",
          path: 'egypt',
          room: 'à la Mezzanine'
        },
        {
          name: "JVtown",
          path: 'japan',
          room: 'à la Terrasse'
        },
        {
          name: "Devopolis",
          path: 'russia',
          room: 'à la Cafet'
        },
      ]
    };
  },
}
</script>

<style lang="scss">

@import "~/static/scss/main.scss";

</style>
