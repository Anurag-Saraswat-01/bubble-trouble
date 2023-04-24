<script>
import { ref } from "vue";
import Bubble from "./Bubble.vue";
import Header from "./Header.vue";
import Footer from "./Footer.vue";

export default {
  components: {
    Bubble,
    Header,
    Footer,
  },
  setup() {
    const bubbles = ref({});
    const count = ref(0);

    setInterval(() => {
      bubbles.value[count.value] = count.value;
      //   console.log("Bubble generated", count.value);
      let tempCount = count.value;
      setTimeout(() => {
        // console.log("Timeout", tempCount);
        delete bubbles.value[tempCount];
      }, 13000);
      count.value++;
    }, 1500);

    function popBubble(id) {
      delete bubbles.value[id];
      //   console.log("Bubble popped", id);
      //   console.log(Object.keys(bubbles.value));
    }

    return { bubbles, popBubble };
  },
};
</script>

<template>
  <div class="bubble-container">
    <Header />
    <div class="bubble-wrapper">
      <div v-for="bubble in Object.keys(bubbles)">
        <Bubble :id="bubbles[bubble]" @pop="popBubble" />
      </div>
    </div>
    <Footer />
  </div>
</template>

<style scoped>
.bubble-container {
  position: relative;
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}
</style>
