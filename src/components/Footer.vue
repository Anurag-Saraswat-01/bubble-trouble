<template>
  <footer>
    Made by
    <a
      href="https://anurag-saraswat-01.github.io/"
      target="_blank"
      rel="noopener noreferrer"
      >Anurag Saraswat</a
    >
    using
    <a href="https://vuejs.org/" target="_blank" rel="noopener noreferrer"
      >VueJS</a
    >
  </footer>
</template>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600&display=swap");

footer {
  color: #b9eddd;
  font-family: "Open Sans", sans-serif;
  font-weight: 600;
  position: absolute;
  width: 100%;
  bottom: 0;
  padding: 0.5rem 0;
  font-size: 12px;
}

a,
a:visited {
  color: #00ffca;
  text-decoration: none;
}

a:hover,
a:active,
a:focus {
  text-decoration: underline;
}

@media screen and (min-width: 992px) {
  footer {
    font-size: 16px;
  }
}
</style>
