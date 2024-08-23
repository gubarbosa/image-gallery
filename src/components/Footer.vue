<template>
  <footer>
    <img alt="image gallery logo" class="logo" src="@/assets/anonymous.png" width="50" height="50" />
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/images">Images</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/gallery">Gallery</RouterLink>
    </nav>
  </footer>
</template>


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
}

.logo {
  display: block;
  margin: 0 auto 2rem;
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


