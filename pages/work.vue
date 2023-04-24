<template>
  <div class="content">
    <Navigation />
    <Footer />
  </div>
</template>
  
<script>
import Footer from '../components/Footer.vue';
import Navigation from '../components/Navigation.vue';

export default {
  components: { Navigation, Footer },
  head: {
    title: "Mijn werk | Lucas van Borkulo"
  },
}
</script>
<style scoped lang="scss"></style>
  