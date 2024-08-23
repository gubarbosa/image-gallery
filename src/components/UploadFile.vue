<script setup>
import { ref } from 'vue';

const galleryImg = ref([]);
let imageCount = 1;
const personName = 'pessoa'; // Pode ser substituído pelo nome desejado

function handleInsert(event) {
  const files = event.target.files;
  if (files) {
    Array.from(files).forEach(file => {
      if (file.type === 'image/jpeg') {
        const reader = new FileReader();
        reader.onload = (e) => {
          const newImage = {
            src: e.target.result,  // O resultado é a imagem em base64
            name: `${personName}${imageCount++}.jpg`
          };
          galleryImg.value.push(newImage);  // Adiciona a imagem na galeria temporária
        };
        reader.readAsDataURL(file);  // Lê o conteúdo do arquivo
      }
    });
  }
}

function handleRemove(index) {
  galleryImg.value.splice(index, 1);  // Remove a imagem da galeria
}
</script>

<template>
  <div>
    <input type="file" accept="image/jpeg" @change="handleInsert" multiple>
  </div>

  <div class="gallery">
    <div class="gallery-item" v-for="(img, index) in galleryImg" :key="index">
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

.gallery-item button {
  position: absolute;
  top: 5px;
  right: 5px;
  background-color: rgba(255, 255, 255, 0.7);
  border: none;
  padding: 5px;
  cursor: pointer;
}
</style>
