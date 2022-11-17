<template>
   <footer>
    <div class="time-line">
      <div class="time-round"></div>
    </div>

    <div class="footer-description">
      <nuxt-img class="logo-iimventure" src='/img/logo-imventure.png' />
    </div>
  </footer>
</template>

<script>

export default {
  name: 'TheFooter',
  data() {
    return {};
  },
  methods: {}
}

</script>

<style scoped lang='scss'>

@import "~/static/scss/main.scss";

.time-line{
  position: absolute;
  right: 20%;
  height: 50%;
  top: 0;
  width: 2px;
  background: $color-white;
  .time-round{
    position: absolute;
    top: 100%;
    border-radius: 50%;
    width: 10px;
    aspect-ratio: 1 / 1;
    background: $color-white;
    right: calc(20% - 4px);
  }
}

footer {
  margin-top: 80px;
  height: 100vh;
  position: relative;
  .footer-description{
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
