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
    </div>
  </div>
</template>

<style scoped>
.gallery {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 15px;
  padding: 20px;
  padding-top: 110px; /* Ajuste conforme a altura do seu footer */
  box-sizing: border-box;
  justify-items: center; /* Centraliza os itens horizontalmente */
  align-items: center;   /* Centraliza os itens verticalmente */
}

@media (max-width: 1024px) {
  .gallery {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 768px) {
  .gallery {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .gallery {
    grid-template-columns: 1fr;
  }
}

.gallery-item {
  position: relative;
  width: 100%;
  height: 150px; /* Aumentado para melhor visualização */
  overflow: hidden;
  border-radius: 8px; /* Cantos arredondados */
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1); /* Sombra suave */
  transition: transform 0.3s ease; /* Transição suave */
}

.gallery-item:hover {
  transform: scale(1.05); /* Efeito de zoom ao passar o mouse */
}

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 8px; /* Mesmos cantos arredondados da galeria */
  transition: opacity 0.4s ease; /* Transição suave para a opacidade */
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6); /* Fundo mais escuro */
  opacity: 0;
  transition: opacity 0.3s ease;
  color: #fff;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7); /* Sombra do texto mais pronunciada */
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  border-radius: 8px; /* Mesmos cantos arredondados da galeria */
}

.gallery-item:hover .overlay {
  opacity: 1; /* Mostra overlay ao passar o mouse */
}

.add-button {
  grid-column: span 4;
  text-align: center;
  margin-top: 20px;
}


.add-button label {
  padding: 12px 24px; /* Aumentado para um botão mais fácil de clicar */
  font-size: 18px; /* Tamanho da fonte aumentado */
  background-color: #007BFF;
  color: white;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s ease, transform 0.3s ease; /* Transição suave */
}

.add-button label:hover {
  background-color: #0056b3;
  transform: scale(1.05); /* Efeito de zoom no botão ao passar o mouse */
}

</style>
