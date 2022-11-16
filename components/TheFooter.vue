<template>
   <footer>
    <div class="time-line">
      <div class="time-round"></div>
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

footer{
  height: 100vh;
  position: relative;
}

</style>
