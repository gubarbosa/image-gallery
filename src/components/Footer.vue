<template>
  <footer :class="{ hidden: isHidden }">
    <img alt="image gallery logo" class="logo" src="@/assets/anonymous.png" width="50" height="50" />
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/images">Images</RouterLink>
      <RouterLink to="/gallery">Gallery</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </footer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isHidden = ref(false);
let lastScrollTop = 0;

function handleScroll() {
  const currentScrollTop = window.pageYOffset || document.documentElement.scrollTop;
  isHidden.value = currentScrollTop > lastScrollTop;
  lastScrollTop = currentScrollTop;
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll);
});
</script>

<style scoped>
footer {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #333;
  color: #fff;
  padding: 1rem;
  text-align: center;
  transition: transform 0.3s ease-in-out;
  z-index: 1000;
  
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.5); /* Para dar uma sombra */
}


footer.hidden {
  transform: translateY(-100%);
}

.logo {
  display: block;
  margin: 0 auto 1rem;
  filter: drop-shadow(0 0 10px rgba(0, 0, 0, 0.75));
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 1rem;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid #fff;
}

nav a:first-of-type {
  border: 0;
}
</style>
