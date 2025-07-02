<template>
  <section class="introduction" id="library">
    <div class="background-overlay"></div>
    <div class="content-container">
      <h1 class="intro-title">MOVIE&nbsp;LIBRARY</h1>
      <p class="intro-text">
        Lorem ipsum dolor sit amet, consectetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
      </p>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Introduction'
};
</script>

<style scoped>
.introduction {
  position: relative;
  min-height: 60vh;
  background: linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)),
              url('https://images.unsplash.com/photo-1489599735946-9a65be818e45?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80') center/cover;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  color: white;
  overflow: hidden;
  width: 100%;
}

.background-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.4);
}

.content-container {
  position: relative;
  z-index: 2;
  max-width: 600px;
  padding: 0 10%;
  text-align: left;
}

.intro-title {
  font-size: 3rem;
  margin-bottom: 30px;
  color: #ffffff;
  font-weight: 700;
  letter-spacing: 1px;
  text-transform: uppercase;
  white-space: nowrap;
}

.intro-text {
  font-size: 1.1rem;
  line-height: 1.8;
  color: rgba(255, 255, 255, 0.9);
  font-weight: 300;
  max-width: 500px;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

@media (max-width: 768px) {
  .intro-title {
    font-size: 2rem;
    margin-bottom: 20px;
  }
  
  .intro-text {
    font-size: 1.1rem;
    padding: 0 20px;
  }
  
  .introduction {
    padding: 40px 0;
  }
}

@media (max-width: 480px) {
  .intro-title {
    font-size: 1.8rem;
  }
  
  .intro-text {
    font-size: 1rem;
  }
}
</style>
