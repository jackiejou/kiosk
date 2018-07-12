<template>
  <div>
    <transition name="fade" mode="out-in">
      <img id="slideshow" :src="currentImage">
    </transition>
    <h1 id="title">
      Random.co Registration Kiosk
    </h1>
  </div>
</template>

<script>
export default {
  name: 'Slideshow',
  data: function () {
    return {
      images: [
        "https://images.pexels.com/photos/681336/pexels-photo-681336.jpeg",
        "https://images.pexels.com/photos/237272/pexels-photo-237272.jpeg",
        "https://images.pexels.com/photos/726298/pexels-photo-726298.jpeg",
        ],
      index: 0,
    }
  },
  methods: {
    start: function() {
      setInterval(this.next, 7000);
    },
    next: function() {
      this.index++;
    }
  },
  computed: {
    currentImage: function() {
      return this.images[this.index % this.images.length];
    }
  },
  mounted: function() {
    this.start();
  }
}
</script>

<style>
#slideshow {
  height: 100vh;
  width: 100%;
  margin: 0;
  position: relative;
  margin: auto;
}
.fade-enter-active, .fade-leave-active {
  transition: all 0.8s ease;
  opacity: 1;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
#title {
  position: absolute;
  top: 10%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  text-shadow: 0 0 5px black;
}
</style>
