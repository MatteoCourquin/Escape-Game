<template>
  <div class="parallax-section" :id="'parallax-section' + id">
    <div class="time-line">
      <div class="time-round"></div>
    </div>

    <div :class="'parallax-bg' + id" data-speed=".75">
      <div>{{pays}}</div>
    </div>
    <div :class="'parallax-bg' + id" data-speed=".4">
      <div>{{pays}}</div>
    </div>
    <div :class="'parallax-bg' + id" data-speed=".25">
      <div>{{pays}}</div>
    </div>
  </div>
</template>

<script>

import { gsap } from "gsap";
import ScrollTrigger from "gsap/dist/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

export default {
  name: "Component",
  props: {
    id: Number,
    pays: String,
  },
  data() {
    return {};
  },
  methods: {
    parallax() {

      gsap.utils.toArray(".parallax-section").forEach((section) => {
        gsap.utils.toArray(".parallax-bg" + this.id).forEach((layer) => {
          gsap.to(layer, {
            scrollTrigger: {
              trigger: section,
              start: "50% 50%",
              // end: "bottom bottom",
              markers: true,
              scrub: true
            },
            y: (i, target) => -(ScrollTrigger.maxScroll(window) * target.dataset.speed) / 2,
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
  height: 101vw;
  width: 2px;
  background: $color-white;
  .time-round{
    position: absolute;
    top: 50%;
    border-radius: 50%;
    width: 10px;
    aspect-ratio: 1 / 1;
    background: $color-white;
    right: calc(20% - 4px);
  }
}

.parallax-section{
  overflow: hidden;
  border: 2px solid black;
  display: flex;
  justify-content: end;
  align-items: center;
  flex-direction: column;
  height: 150vh;
}

</style>
