<template>
  <div>
    <TheHeader />
    <Hero />
    <Component v-for="(pays, i) in pays" :pays=pays.pays :id=i+1 />
  </div>
</template>

<script>

import TheHeader from '../components/TheHeader.vue';
import Hero from '../components/Hero.vue';
import Component from '../components/Component.vue';

export default {
  name: "IndexPage",
  components: { TheHeader, Hero, Component },
  data() {
    return {
      pays: [
        {
          pays: "États-Unis",
        },
        {
          pays: "inde",
        },
        {
          pays: "Égypte",
        },
        {
          pays: "Japon",
        },
        {
          pays: "Russie",
        },
      ]
    };
  },
}
</script>

<style lang="scss">

@import "~/static/scss/main.scss";

</style>
