<script setup>
import { ref } from 'vue';

function generateImageList(count) {
  const images = [];
  for (let i = 1; i <= count; i++) {
    images.push({ src: new URL(`../assets/gallery_img/pessoa${i}.jpg`, import.meta.url).href });
  }
  return images;
}

const images = ref(generateImageList(20));
</script>

<template>
  <div class="gallery">
    <div class="gallery-item" v-for="(image, index) in images" :key="index"> 
      <img :src="image.src" :alt="'Image ' + (index + 1)">
      <div class="overlay">Image {{ index + 1 }}</div>
    </div>

    <!-- Estas imagens adicionais podem ser removidas, pois já estão incluídas no loop dinâmico -->
  </div>
</template>

<style scoped>
.gallery {
  position: relative;
  display: flex; 
  flex-wrap: wrap;
  justify-content: center;
  padding: 20px;
}

.gallery-item {
  position: relative;
  width: 120px;
  height: 120px;
  margin: 2px;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.gallery-item img {
  width: 100%;
  height: 100%;
  transition: transform 0.4s ease;
  position: absolute; 
  top: 0;
  left: 0;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  opacity: 0;
  transition: opacity 0.3s ease;
  color: #fff;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.gallery-item:hover img {
  transform: scale(1.1);
}

.gallery-item:hover .overlay {
  opacity: 1;
}
</style>
