<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
<div class="wapper">
    <Header />
    <div class="wrapper-content">
      <div class="container">
        <router-view />
      </div>
    </div>
    <Footer />
  </div>
</template>
<script>
import Header from "../src/components/Header.vue";
import Footer from "../src/components/Footer.vue";

export default {
  components: {
    Header,
    Footer,
  },
};
</script>
