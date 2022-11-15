<template>
  <header>
    <ul>
      <li><a href="#">États-Unis</a></li>
      <li><a href="#">Inde</a></li>
      <li><a href="#">Égypte</a></li>
      <li><a href="#">Japon</a></li>
      <li><a href="#">Russie</a></li>
    </ul>
  </header>
</template>

<script>

export default {
  name: "TheHeader",
  data() {
    return {};
  },
  methods: {}
}

</script>

<style scoped lang='scss'>

header{
  height: 80px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  ul{
    list-style-type: none;
    margin-left: 10%;
    li{
      display: inline;
      &:not(:last-child){
        margin-right: 30px;
      }
    }
  }
}

</style>
