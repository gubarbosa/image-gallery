<script setup>
import { ref } from 'vue';
import Footer from '@/components/Footer.vue';

const galleryImg = ref([]);
let imageCount = 19; // Começa em 19, assumindo que você já tem 18 imagens.
const personName = 'Leonardo'; // Pode ser substituído pelo nome desejado

function generateImageList(count) {
  const images = [];
  for (let i = 1; i <= count; i++) {
    images.push({ src: new URL(`../assets/gallery_img/pessoa${i}.jpg`, import.meta.url).href });
  }
  return images;
}

function handleInsert(event) {
  const files = event.target.files;
  if (files) {
    Array.from(files).forEach(file => {
      if (file.type === 'image/jpeg') {
        const reader = new FileReader();
        reader.onload = (e) => {
          const newImage = {
            src: e.target.result,
            name: `${personName}${imageCount++}.jpg`
          };
          galleryImg.value.push(newImage);
        };
        reader.readAsDataURL(file);
      }
    });
  }
}

function handleRemove(index) {
  galleryImg.value.splice(index, 1);
}

const images = ref(generateImageList(18));
</script>

<template>
  <Footer></Footer>
 

  <div class="gallery">


    <!-- Botão de adicionar imagens -->
    <div class="add-button">
      <input type="file" accept="image/jpeg" @change="handleInsert" multiple>
      <button>Add Image</button>
    </div>

    <!-- Imagens já existentes na galeria -->
    <div class="gallery-item" v-for="(image, index) in images" :key="index">
      <img :src="image.src" :alt="'Image ' + (index + 1)">
      <div class="overlay">Image {{ index + 1 }}</div>
    </div>

        <!-- Imagens novas adicionadas através do UploadFile -->
    <div class="gallery-item" v-for="(img, index) in galleryImg" :key="index + images.length">
      <img :src="img.src" :alt="img.name">
      <p>{{ img.name }}</p>
      <button @click="handleRemove(index)">Remove</button>
    </div>
  </div>
</template>

<style scoped>
.gallery {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
  padding: 20px;
  padding-top: 110px; /* Ajuste conforme a altura do seu footer */
  box-sizing: border-box;
}

.gallery-item {
  position: relative;
  width: 100%;
  height: 120px;
  overflow: hidden;
}

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
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

.add-button {
  grid-column: span 4;
  text-align: center;
  margin-top: 20px;
}

.add-button button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
</style>
