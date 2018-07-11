<template>
  <div id="app">
    <button v-on:click="showModal">Sign Up</button>
    <signup v-if="show"/>
  </div>
</template>

<script>
import Signup from './components/Signup'

export default {
  name: 'app',
  components: {
    Signup
  },
  data() {
    return {
      show: false,
    }
  },
  methods: {
    showModal: function() {
      this.show = true;
    },
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
