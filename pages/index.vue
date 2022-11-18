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
import paysJson from "../static/data/pays.json";

export default {
  name: "IndexPage",
  components: { TheHeader, Hero, Parallax, TheFooter },
  data() {
    return {
      pays: []
    };
  },
  beforeMount() {
    this.pays = paysJson;
  }
}
</script>

<style lang="scss">

@import "~/static/scss/main.scss";

</style>
