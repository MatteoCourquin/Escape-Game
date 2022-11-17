<template>
  <div class="hero">
    <div class="time-line">
      <div class="time-round"></div>
    </div>

    <div class="hero-description">
      <nuxt-img class="logo-iimventure" src="/img/logo-iimventure.png" />
      <p>
        Le fameux Pesaro te mettra au défi d'embarquer dans une aventure pour un
        escape game unique à l'intérieur du campus de l'arche IIM.
        <br>
        <br>
        Challenge ton esprit de futur expert du digital à travers 5 univers
        épiques. Pesaro compte sur toi, alors n'attend plus et commence
        l'aventure !
      </p>
      <div>
        <button class="button button-white" @click="togglePopUpVideo">
          Commencer l'aventure
        </button>
        <button class="button button-transparent" @click="scroll">Go</button>
      </div>
    </div>

    <div class="pop-up-video" @click="togglePopUpVideo">
      <video controls width="250" id="video-pitch">
        <source src="~/static/video/video-pitch.mp4" type="video/mp4" />
      </video>
    </div>
  </div>
</template>

<script>
export default {
  name: "Hero",
  data() {
    return {};
  },
  methods: {
    scroll() {
      let pageHeight = window.innerHeight;
      window.scrollBy(0, pageHeight);
    },
    togglePopUpVideo() {
      const popUpVideo = document.querySelector(".pop-up-video");
      const video = document.querySelector("#video-pitch");

      popUpVideo.classList.contains("active")
        ? (popUpVideo.classList.remove("active"), video.pause())
        : (popUpVideo.classList.add("active"), video.play());

      video.addEventListener("ended", () => {
        const popUpVideo = document.querySelector(".pop-up-video");
        popUpVideo.classList.remove("active");
      });
    },
  },
};
</script>

<style scoped lang="scss">
@import "~/static/scss/main.scss";

.time-line {
  position: absolute;
  right: 20%;
  height: 50%;
  bottom: 0;
  width: 2px;
  background: $color-white;
  .time-round {
    position: absolute;
    bottom: 100%;
    border-radius: 50%;
    width: 10px;
    aspect-ratio: 1 / 1;
    background: $color-white;
    right: calc(20% - 4px);
  }
}

.hero {
  margin-top: 80px;
  height: calc(100vh - 80px);
  position: relative;
  .hero-description {
    display: flex;
    justify-content: center;
    flex-direction: column;
    height: 100%;
    margin: clamp(20px, 10vw, 100px);
    width: 50%;
    .logo-iimventure {
      width: 80%;
    }
    p {
      font-size: 1.1rem;
      font-family: $font-roboto-medium;
      margin: clamp(20px, 2vw, 30px) 0;
    }
    .button:nth-child(1) {
      margin-right: 20px;
    }
  }
}

.pop-up-video.active {
  display: flex;
  opacity: 1;
  z-index: 80;
  video {
    transform: scale(1);
  }
}
.pop-up-video {
  position: fixed;
  transition: opacity 0.2s ease;
  opacity: 0;
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: #122547ae;
  z-index: -1;
  video {
    transition: transform 0.5s ease;
    width: 60%;
    transform: scale(0);
    @include respoXL {
      width: 90%;
    }
  }
}
</style>
