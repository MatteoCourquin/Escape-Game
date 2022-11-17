<template>
  <header>
    <ul>
      <li v-for="(pays, i) in pays"><a class="link" :href="'#' + pays.path">{{pays.name}}</a></li>
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
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  position: fixed;
  width: 100%;
  height: 80px;
  top: 0;
  display: flex;
  justify-content: flex-end;
  align-items: center;
  ul{
    list-style-type: none;
    margin-right: 10%;
    li{
      display: inline;
      &:not(:last-child){
        margin-right: 30px;
      }
    }
  }
}

</style>
