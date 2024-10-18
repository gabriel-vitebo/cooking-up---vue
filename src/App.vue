<script lang="ts">
import Banner from './components/Banner.vue'
import MainContent from './components/MainContent.vue';
import Footer from './components/Footer.vue'

export default {
  components: { Footer, Banner, MainContent }
}
</script>

<template>
  <Banner />
  <MainContent />
  <Footer />
</template>

<style scoped></style>