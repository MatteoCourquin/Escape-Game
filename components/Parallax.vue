<template>
  <div class="container-parallax-section">
    <section v-for="(pays, i) in pays" class="parallax-section" :id="`${pays.path}`" >
      <div class="time-line">
        <div class="time-line-round">
          <span class="time-line-pays">{{pays.name}}</span>
        </div>
      </div>

      <nuxt-img :class="'img-asset1 parallax-bg' + id" data-speed=".18" :src="`/img/parallax/${pays.path}/asset1.png`" />
      <nuxt-img :class="'img-asset2 parallax-bg' + id" data-speed=".08" :src="`/img/parallax/${pays.path}/asset2.png`" />
      <nuxt-img :class="'img-asset3 parallax-bg' + id" data-speed=".02" :src="`/img/parallax/${pays.path}/asset3.png`" />
    </section>
  </div>
</template>

<script>

import { gsap } from "gsap";
import ScrollTrigger from "gsap/dist/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "Parallax",
  props: {
    pays: Array,
  },
  data() {
    return {};
  },
  methods: {
    parallax() {

      gsap.utils.toArray(".parallax-section").forEach((section) => {
        gsap.from(section.querySelectorAll(".parallax-bg"), {
          opacity: 0,
          ease: "none",
        });
        gsap.utils.toArray(".parallax-bg" + this.id).forEach((layer) => {
          gsap.to(layer, {
            scrollTrigger: {
              trigger: section,
              start: "50% 50%",
              end: "bottom top",
              markers: true,
              scrub: true
            },
            y: (i, target) => -5000 * target.dataset.speed,
            ease: "out"
          });
        });
      });
    },
  },
  mounted() {
    this.parallax()
  }
}

</script>

<style scoped lang='scss'>

@import "~/static/scss/main.scss";

.time-line{
  position: absolute;
  right: 20%;
  top: 0;
  height: 100%;
  width: 2px;
  background: $color-white;
  z-index: 50;
  .time-line-round{
    position: absolute;
    top: 30%;
    border-radius: 50%;
    width: 10px;
    aspect-ratio: 1 / 1;
    background: $color-white;
    right: calc(20% - 4px);
    .time-line-pays{
      position: absolute;
      white-space: nowrap;
      font-size: clamp(1.6rem, 3vw, 4rem);
      transform: translate(calc(-100% + -20px), -50%);
    }
  }
}

.container-parallax-section{
  background: linear-gradient(180deg, #172547 0%, #5B7C92 10%, #172547 20%, #2F5394 30%, #172547 40%, #310DA7 50%, #172547 60%, #D41C5C 70%, #172547 80%, #467E95 90%, #172547 100%);
}

.parallax-section{
  position: relative;
  flex-direction: column;
  height: 200vh;

  img{
    width: 100%;
    position: absolute;
    bottom: 0;
  }
  .img-asset1{
    z-index: 30;
    bottom: -40%;
  }
  .img-asset2{
    z-index: 20;
    bottom: -20%;
  }
  .img-asset3{
    z-index: 10;
    bottom: -0%;
  }
}

</style>
