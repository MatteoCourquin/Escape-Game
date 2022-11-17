<template>
  <div class="container-parallax-section">
    <section
      v-for="(pays, i) in pays"
      class="parallax-section"
      :id="`${pays.path}`"
    >
      <div class="time-line">
        <div class="time-line-round">
          <span class="time-line-pays">{{ pays.name }}</span>
          <span class="time-line-room">Rendez-vous {{ pays.room }}</span>
        </div>
      </div>

      <nuxt-img
        :class="'img-asset1 parallax-item' + id"
        data-speed=".16"
        :src="`/img/parallax/${pays.path}/asset1.png`"
      />
      <nuxt-img
        :class="'img-asset2 parallax-item' + id"
        data-speed=".08"
        :src="`/img/parallax/${pays.path}/asset2.png`"
      />
      <nuxt-img
        :class="'img-asset3 parallax-item' + id"
        data-speed=".02"
        :src="`/img/parallax/${pays.path}/asset3.png`"
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
    parallax() {
      gsap.utils.toArray(".parallax-section").forEach((section) => {
        gsap.utils.toArray(".parallax-item" + this.id).forEach((layer) => {
          gsap.to(layer, {
            scrollTrigger: {
              trigger: section,
              start: "60% 50%",
              end: "bottom top",
              scrub: true,
            },
            y: (i, target) => -5000 * target.dataset.speed,
            ease: "out",
          });
        });
      });
    },
  },
  mounted() {
    this.parallax();
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
  .time-line-round {
    position: absolute;
    top: 30%;
    border-radius: 50%;
    width: 10px;
    aspect-ratio: 1 / 1;
    background: $color-white;
    right: calc(20% - 4px);
    .time-line-pays {
      position: absolute;
      white-space: nowrap;
      font-size: clamp(1.6rem, 3vw, 4rem);
      transform: translate(calc(-100% + -20px), -50%);
    }
    .time-line-room{
      position: absolute;
      white-space: nowrap;
      font-family: $font-roboto-regular;
      transform: translate(calc(-100% + -20px), calc(100% + 20px));
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

  img{
    width: 100%;
    position: absolute;
  }
  .img-asset1 {
    width: 30%;
    z-index: 30;
    left: 0%;
    bottom: 5%;
  }
  .img-asset2 {
    z-index: 20;
    bottom: -25%;
  }
  .img-asset3 {
    z-index: 10;
    bottom: 0%;
  }
  @media screen and (max-width: 1300px) {
    .img-asset1 {
      bottom: -40%;
    }
    .img-asset2 {
      bottom: -20%;
    }
    .img-asset3 {
      bottom: 0%;
    }
  }
  @media screen and (max-width: 600px) {
    .img-asset1 {
      bottom: -40%;
    }
    .img-asset2 {
      bottom: -15%;
    }
    .img-asset3 {
      bottom: 0%;
    }
  }
}
</style>
