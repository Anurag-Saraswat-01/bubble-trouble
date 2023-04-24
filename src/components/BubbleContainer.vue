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
      count.value++;
    }, 2000);

    function popBubble(idx) {
      bubbles.value[idx] = null;
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
        <Bubble :idx="bubbles[bubble]" @pop="popBubble" />
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
