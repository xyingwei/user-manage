<template>
  <div class="hello">
    {{msg}}
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
  .hello {
    width: 200px;
    height: 40px;
    background-color:pink;
    margin: 0 auto;
  }
</style>
