<script setup></script>
<template>
  <div class="bubble"></div>
</template>
<style scoped>
.bubble {
  position: absolute;
  background: radial-gradient(
    circle at 50% 50%,
    rgba(255, 255, 255, 0.2),
    transparent
  );
  box-shadow: inset 2px 2px 10px white, inset -1px -1px 2px red,
    inset -1px 0 2px orange, inset 0 -1px 2px yellow, inset -2px 0 2px green,
    inset 0 -2px 2px blue, inset -2px -3px 3px indigo,
    inset -3px -2px 3px violet, 0 0 10px rgba(255, 255, 255, 0.2);
  border-radius: 100%;
  width: 100px;
  height: 100px;
  animation: float 12s infinite ease-in-out,
    sway 3s infinite ease-in-out alternate;
  -moz-animation: float 12s infinite ease-in-out,
    sway 3s infinite ease-in-out alternate;
  -webkit-animation: float 12s infinite ease-in-out,
    sway 3s infinite ease-in-out alternate;
  /* animation:  */
}

@keyframes float {
  0% {
    top: 100%;
  }
  100% {
    top: -100px;
  }
}

@-moz-keyframes float {
  0% {
    bottom: 0;
  }
  100% {
    top: 0;
  }
}

@-webkit-keyframes float {
  0% {
    bottom: 0;
  }
  100% {
    top: 0;
  }
}

@keyframes sway {
  0% {
    transform: translateX(-50%);
  }
  100% {
    transform: translateX(50%);
  }
}

@-moz-keyframes sway {
  0% {
    transform: translateX(-50%);
  }
  100% {
    transform: translateX(50%);
  }
}

@-webkit-keyframes sway {
  0% {
    transform: translateX(-50%);
  }
  100% {
    transform: translateX(50%);
  }
}
</style>
