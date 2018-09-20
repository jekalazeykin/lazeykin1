<template>
<div id="app">
  <Header></Header>
  <router-view/>
  <Footer></Footer>
</div>
</template>

<script>
import Header from '@/components/Header';
import Footer from '@/components/Footer';

export default {
  name: 'App',
  components: {
    Header,
    Footer
  }
}
</script>

<style>
@import "./assets/normalize.css";
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
}
</style>
