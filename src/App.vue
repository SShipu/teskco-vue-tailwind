<template>
    <Header />
    <RouterView />
    <Footer />
</template>

<script setup>
import { RouterView } from 'vue-router';
import Header from './components/header/Header.vue';
import Footer from './components/Footer.vue';
import { onMounted } from 'vue';

onMounted(() => {
  const meta = document.querySelector("meta[name='description']");
  const descriptionContent = 'Explore popular subjects students are choosing worldwide. Find top courses and learn more about each subject area.';
  document.title = 'Explore Popular Subjects | EHL Course Finder';
  
  if (meta) {
    meta.setAttribute('content', descriptionContent)
  } else {
    const metaTag = document.createElement('meta')
    metaTag.name = 'description'
    metaTag.content = descriptionContent
    document.head.appendChild(metaTag)
  }
})
</script>

<style scoped></style>
