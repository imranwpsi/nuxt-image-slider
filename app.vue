<template>
  <div class="image-slider">
    <div class="slider-container">
      <img :src="images[currentSlide]" />
    </div>
    <button 
      class="prev-button"
      :class="prevButtonDisabled ? 'disabled' : ''"
      @click="prevSlide"
    >&#8249;</button>
    <button 
      class="next-button"
      :class="nextButtonDisabled ? 'disabled' : ''"
      @click="nextSlide"
    >&#8250;</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
        '/img/slider/1.jpg',
        '/img/slider/2.jpg',
        '/img/slider/3.jpg',
        // Add more image paths as needed
      ],
      currentSlide: 0
    };
  },
  computed: {
    prevButtonDisabled() {
      return this.currentSlide === 0;
    },
    nextButtonDisabled() {
      return this.currentSlide === this.images.length - 1;
    },
  },
  methods: {
    prevSlide() {
      if (this.currentSlide > 0) {
        this.currentSlide--;
      }
    },
    nextSlide() {
      console.log('next slide');
      if (this.currentSlide < this.images.length - 1) {
        this.currentSlide++;
      }
    },
  },
};
</script>

<style scoped>
.image-slider {
  position: relative;
  max-width: 800px;
  margin: 0 auto;
  overflow: hidden;
}

.slider-container {
  display: flex;
  transition: transform 0.5s ease-in-out;
  height: 100vh;
}

.slide {
  flex: 0 0 100%;
}

img {
  width: 100%;
  height: auto;
}

.prev-button,
.next-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: rgba(0, 0, 0, 0.4);
  color: #fff;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 30px;
}

.prev-button {
  left: 0;
}

.next-button {
  right: 0;
}
.prev-button.disabled, .next-button.disabled {
  color: #aaa;
}
</style>
