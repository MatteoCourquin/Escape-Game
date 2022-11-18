<template>
   <footer>
    <div class="time-line">
      <div class="time-round"></div>
    </div>

    <div class="footer-description">
      <nuxt-img class="logo-iimventure" src='/img/logo-iimventure-small.png' />
      <p>Félicitations ! Tu as su résoudre les énigmes de l'IIMventure. Garde encore un peu de jugeote pour compléter le TotIIM, qui te permettra de rejoindre ton axe préféré au sein de l'IIM.</p>
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
    height: 10px;
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
    align-items: center;
    height: 100%;
    margin: clamp(20px, 10vw, 100px);
    width: 50%;

    @include respoM{
      width: 60%;
      flex-direction: column;
      justify-content: center;
    }
    .logo-iimventure{
      width: 200px;
      margin-right: clamp(20px, 5vw, 100px);
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
