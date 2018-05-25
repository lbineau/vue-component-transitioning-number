<template>
  <div id="app">
    <input type="number" name="" id="" v-model="value" min="0" max="9">
    Price: <TransitioningNumber :end-value="value" />€
  </div>
</template>

<script>
import TransitioningNumber from './components/TransitioningNumber.vue'

export default {
  name: 'app',
  data () {
    return {
      value: 8
    }
  },
  components: {
    TransitioningNumber
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 6em;
  input {
    display: block;
    font-size: 1em;
    margin: 0 auto;
  }
}
</style>
