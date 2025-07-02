<template>
  <section class="hero" id="hero">
    <div class="carousel-container">
      <div class="carousel-slide" :class="{ active: currentSlide === 0 }">
        <img src="../../public/Assets/Images/Header_Image.jpg" alt="Cinema Theater" class="carousel-image" />
        <div class="slide-overlay"></div>
        <div class="slide-content"></div>
      </div>
      
      <div class="carousel-slide" :class="{ active: currentSlide === 1 }">
        <video 
          src="../../public/Assets/Videos/Header Video.mp4" 
          class="carousel-image" 
          autoplay 
          muted 
          loop
        >
          Your browser does not support the video tag.
        </video>
        <div class="slide-overlay"></div>
        <div class="slide-content">
        </div>
      </div>

      <!-- Navigation dots -->
      <div class="carousel-dots">
        <button 
          v-for="(slide, index) in totalSlides" 
          :key="index"
          class="dot"
          :class="{ active: currentSlide === index }"
          @click="goToSlide(index)"
        ></button>
      </div>

      <!-- Navigation arrows -->
      <button class="carousel-arrow prev" @click="prevSlide">‹</button>
      <button class="carousel-arrow next" @click="nextSlide">›</button>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Hero',
  data() {
    return {
      currentSlide: 0,
      totalSlides: 2,
      autoplayInterval: null
    };
  },
  mounted() {
    this.startAutoplay();
  },
  beforeUnmount() {
    this.stopAutoplay();
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.totalSlides;
    },
    prevSlide() {
      this.currentSlide = this.currentSlide === 0 ? this.totalSlides - 1 : this.currentSlide - 1;
    },
    goToSlide(index) {
      this.currentSlide = index;
    },
    startAutoplay() {
      this.autoplayInterval = setInterval(() => {
        this.nextSlide();
      }, 5000);
    },
    stopAutoplay() {
      if (this.autoplayInterval) {
        clearInterval(this.autoplayInterval);
      }
    }
  }
};
</script>

<style scoped>
.hero {
  position: relative;
  min-height: 70vh;
  overflow: hidden;
}

.carousel-container {
  position: relative;
  width: 100%;
  height: 70vh;
}

.carousel-slide {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity 0.5s ease-in-out;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}

.carousel-slide.active {
  opacity: 1;
}

.carousel-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 1;
}

video.carousel-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 1;
}

.slide-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: 2;
}

.slide-content {
  position: relative;
  z-index: 3;
  max-width: 600px;
  padding: 0 60px;
  color: white;
}

.hero-title {
  font-size: 3.5rem;
  margin-bottom: 30px;
  color: #ffffff;
  font-weight: 700;
  letter-spacing: 2px;
  text-transform: uppercase;
}

.hero-text {
  font-size: 1.1rem;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.9);
  font-weight: 300;
}

.carousel-dots {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 12px;
  z-index: 4;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  border: 2px solid rgba(255, 255, 255, 0.5);
  background: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
}

.dot.active {
  background: #f39c12;
  border-color: #f39c12;
}

.carousel-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.5);
  color: white;
  border: none;
  font-size: 24px;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
  transition: background 0.3s ease;
  z-index: 4;
}

.carousel-arrow:hover {
  background: rgba(0, 0, 0, 0.8);
}

.carousel-arrow.prev {
  left: 30px;
}

.carousel-arrow.next {
  right: 30px;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2rem;
    margin-bottom: 20px;
  }
  
  .hero-text {
    font-size: 1rem;
  }
  
  .slide-content {
    padding: 0 30px;
  }
  
  .carousel-arrow {
    width: 40px;
    height: 40px;
    font-size: 20px;
  }
  
  .carousel-arrow.prev {
    left: 15px;
  }
  
  .carousel-arrow.next {
    right: 15px;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 1.8rem;
  }
  
  .hero-text {
    font-size: 0.9rem;
  }
  
  .slide-content {
    padding: 0 20px;
  }
}
</style>
