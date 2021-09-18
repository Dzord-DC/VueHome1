<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App" :is-show="show" />
    <h3 v-if="show">{{ messege }}</h3>
    <button @click="doShow">
      <span v-if="!show">Показать</span> <span v-if="show">Скрыть</span>
    </button>
    <br />
    <calc />
  </div>
</template>

<script>
import Calc from './components/Calc.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Calc
  },
  data: () => ({
    messege: 'Привет',
    show: false
  }),
  methods: {
    doShow () {
      this.show = !this.show
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
