<template>
  <div class="hero">
    <div class="time-line">
      <div class="time-round"></div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Hero',
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
  bottom: 0;
  width: 2px;
  background: $color-white;
  .time-round{
    position: absolute;
    bottom: 100%;
    border-radius: 50%;
    width: 10px;
    aspect-ratio: 1 / 1;
    background: $color-white;
    right: calc(20% - 4px);
  }
}

.hero{
  height: 100vh;
  position: relative;
}

</style>
