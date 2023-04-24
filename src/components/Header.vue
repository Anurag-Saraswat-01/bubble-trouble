<template>
  <nav>
    <h1>Bubble Trouble</h1>
    <h2>Prepare for Trouble. Make it Bubble</h2>
  </nav>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Sigmar&display=swap");

nav {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 0.25rem;
  padding: 0.5rem 0;
  position: relative;
  z-index: 10;
}

h1,
h2 {
  font-family: "Sigmar", cursive;
  color: #b9eddd;
  margin: 0;
}

h1 {
  font-size: 32px;
  text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000,
    1px 1px 0 #000;
}

h2 {
  font-size: 12px;
}

@media screen and (min-width: 992px) {
  nav {
    padding: 1rem;
  }

  h1 {
    font-size: 42px;
  }

  h2 {
    font-size: 16px;
  }
}
</style>
