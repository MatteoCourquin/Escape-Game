<template>
  <div class="hero">
    <div class="time-line">
      <div class="time-round"></div>
    </div>

    <div class="hero-description">
      <nuxt-img class="logo-iimventure" src='/img/logo-imventure.png' />
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Magni eligendi
        rerum ut ipsa quas dolores commodi tempore quisquam. Rerum incidunt
        dolores assumenda praesentium voluptatibus qui vero ipsum itaque soluta
        eius.
      </p>
      <a href="#us"><button>Commencer l'aventure</button></a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Hero",
  data() {
    return {};
  },
  methods: {},
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
  .hero-description{
    display: flex;
    justify-content: center;
    flex-direction: column;
    height: 100%;
    margin: clamp(20px, 10vw, 100px);
    width: 50%;
    .logo-iimventure{
      width: 80%;
    }
    p{
      font-size: 1.1rem;
      font-family: $font-roboto-medium;
      margin: clamp(20px, 2vw, 30px) 0;
    }
    button{
      font-size: 1.1rem;
    }
  }
}
</style>
