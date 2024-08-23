<template>
  <header>
  <img alt="image gallery logo" class="logo" src="@/assets/anonymous.png" width="125" height="125" />

  <div class="wrapper">
    <div class="greetings">
            <h1 class="green">This Person Does Not Exist</h1>
            <p>    This website show images created by AI of people that does not exist.   </p>

    </div>

    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/images">Images</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/gallery">Gallery</RouterLink>
    </nav>
  </div>
  </header>
</template>



<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
  /* box-shadow: 0 0 10px rgba(0, 0, 0, 0.5); */
  /*border: 0.5px solid rgba(0, 0, 0, 0.5); */
  filter: drop-shadow(0 0 10px rgba(0, 0, 0, 0.75));
  /*background-color: rgba(0, 0, 0, 0.1);  */
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
    transition: top 0.3s;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
