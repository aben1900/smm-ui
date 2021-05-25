<template>
  <div id="app" style="margin: 0;">
    <MainPane msg="" style="height: 100%;"/>
  </div>
</template>

<script>
import MainPane from './components/MainPane.vue'

export default {
  name: 'app',
  data(){
    return {
      screenHeight:''
    }
  },
  mounted () {
    const that = this;
    window.onload = () => {
      return (() => {
        var left = document.getElementById("app");
        var height = window.innerHeight-65;
        left.style.height = height +'px'
        left.style.minHeight = 800 + 'px'
        console.log(left.style.height)
      })()
    }
  },
  components: {
    MainPane
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
