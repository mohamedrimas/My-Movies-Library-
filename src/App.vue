<!-- src/App.vue -->
<template>
    <div id="app">
        <Header />
        <Hero />
        <Introduction />
        <MovieGrid />
        <ContactForm />
        <Footer/>
        
    </div>
</template>

<script>
import Header from './components/Header.vue';
import Hero from './components/Hero.vue';
import Introduction from './components/Introduction.vue';
import MovieGrid from './components/MovieGrid.vue';
import ContactForm from './components/ContactForm.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    Hero,
    Introduction,
    MovieGrid,
    ContactForm,
    Footer,
    
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Bahnschrift', sans-serif;
}

body {
  margin: 0;
  font-family: 'Bahnschrift', sans-serif;
  background-color: #111;
}
</style>
