<template>
  <div class="container-parallax-section">
    <section
      v-for="(singlePays, i) in pays"
      :class="'parallax-section parallax-section' + (i + 1)"
      :id="`${singlePays.path}`"
    >
      <div class="time-line"></div>
      <div class="time-line-round">
        <div class="time-line-description">
          <h2 class="time-line-pays">{{ singlePays.name }}</h2>
          <p class="time-line-room">Rendez-vous {{ singlePays.room }}</p>
        </div>
      </div>

      <div :class="'bird parallax-item' + (i + 1)" data-speed=".16">
        <nuxt-img class="bird" :src="`/img/parallax/${singlePays.path}/asset1.png`" />
        <div v-if="singlePays.charade" class="charade">
          <p v-for="(charade) in singlePays.charade">{{charade.text}}</p>
        </div>
      </div>
      <nuxt-img
        :class="'img-asset2 parallax-item' + (i + 1)"
        data-speed=".08"
        :src="`/img/parallax/${singlePays.path}/asset2.png`"
      />
      <nuxt-img
        :class="'img-asset3 parallax-item' + (i + 1)"
        data-speed=".02"
        :src="`/img/parallax/${singlePays.path}/asset3.png`"
      />
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
    startParallax() {
      document.querySelectorAll(".parallax-section").forEach((section, i) => {
        this.parallax(i + 1);
      });
    },
    parallax(i) {
      gsap.to(`.parallax-item${i}`, {
        scrollTrigger: {
          trigger: `.parallax-section${i}`,
          start: "top top",
          end: "bottom top",
          scrub: true,
        },
        y: (i, target) => -5000 * target.dataset.speed,
        ease: "out",
      });
    },
  },
  mounted() {
    this.startParallax();
  },
};
</script>

<style scoped lang="scss">
@import "~/static/scss/main.scss";

.time-line {
  position: absolute;
  right: 20%;
  top: 0;
  height: 120%;
  width: 2px;
  background: $color-white;
  z-index: 50;
}
.time-line-round {
  position: sticky;
  top: 25%;
  left: calc(80% - 2px);
  margin-top: 120px;
  z-index: 50;
  border-radius: 50%;
  width: 10px;
  height: 10px;
  background: $color-white;
  transform: translateX(-40%);
  .time-line-description {
    backdrop-filter: blur(20px);
    box-shadow: $shadow-m;
    position: absolute;
    padding: 10px 20px;
    border-radius: $radius-current;
    border: $border-current;
    transform: translate(calc(-100% + -20px), -50%);
    display: flex;
    justify-content: center;
    align-items: end;
    flex-direction: column;
    .time-line-pays {
      white-space: nowrap;
      font-size: clamp(1.6rem, 3vw, 4rem);
    }
    .time-line-room {
      white-space: nowrap;
    }
  }
}

.container-parallax-section {
  background: linear-gradient(
    180deg,
    #172547 0%,
    #5b7c92 10%,
    #172547 20%,
    #2f5394 30%,
    #172547 40%,
    #310da7 50%,
    #172547 60%,
    #d41c5c 70%,
    #172547 80%,
    #467e95 90%,
    #172547 100%
  );
}

.parallax-section {
  position: relative;
  height: clamp(600px, 200vh, 1700px);

  .bird, .img-asset2, .img-asset3 {
    width: 100%;
    position: absolute;
    bottom: 0;
  }
  .bird {
    width: 50%;
    z-index: 60;
    left: 0%;
    bottom: 40%;
    position: absolute;
    &:hover{
      .charade{
        transform: translate(0) scale(1);
      }
    }
    .charade{
      position: absolute;
      z-index: 99;
      transform: translate(-50%) scale(0);
      transition: transform 0.2s ease;
      bottom: 100%;
      left: 5%;
      backdrop-filter: blur(20px);
      box-shadow: $shadow-m;
      padding: 10px 20px;
      border-radius: $radius-current;
      border: $border-current;
    }
  }
  .img-asset2 {
    z-index: 20;
  }
  .img-asset3 {
    z-index: 10;
    bottom: 20%;
  }
  @include respoM {
    .img-asset1 {
      bottom: 20%;
    }
    // .img-asset2{
    //   bottom: ;
    // }
    .img-asset3 {
      bottom: 10%;
    }
  }
}
</style>
