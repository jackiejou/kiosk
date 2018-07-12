<template>
  <div id="app">
    <slideshow />
    <signup />
  </div>
</template>

<script>
import Signup from './components/Signup';
import Slideshow from './components/Slideshow';

export default {
  name: 'app',
  components: {
    Signup,
    Slideshow,
  },
  data: function() {
    return {
      show: false,
    }
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  position: relative;
}
</style>
