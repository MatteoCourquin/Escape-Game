<template>
  <header>
    <ul>
      <li v-for="(pays, i) in pays"><a :href="'#' + pays.path">{{pays.name}}</a></li>
    </ul>
  </header>
</template>

<script>

export default {
  name: "TheHeader",
  props: {
    pays: Array,
  },
  data() {
    return {};
  },
  methods: {},
}

</script>

<style scoped lang='scss'>

header{
  z-index: 100;
  position: fixed;
  width: 100%;
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
