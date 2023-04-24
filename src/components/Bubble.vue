<script>
import { ref, watch } from "vue";

export default {
  props: {
    idx: Number,
  },
  setup(props, context) {
    const audio = ref(null);
    const bubble = ref(null);
    const size = ref(randomInt(25, 150));
    const pos = ref(randomInt(10, 90));
    const popped = ref(false);

    function randomInt(min, max) {
      return Math.floor(Math.random() * (max - min + 1) + min);
    }

    function playAudio() {
      audio.value.play();

      const poppedBubble = bubble.value;
      poppedBubble.style.animationPlayState = "paused";
      const rect = poppedBubble.getBoundingClientRect();
      poppedBubble.style.top = rect.top.toString() + "px";
      poppedBubble.style.left = rect.left.toString() + "px";
      poppedBubble.classList.remove("floating");
      poppedBubble.style.animationPlayState = "running";
      poppedBubble.classList.add("pop");

      context.emit("pop", props.idx);
      popped.value = true;
      bubble.value.style.display = "none";
    }

    const topPopper = setInterval(() => {
      if (
        !popped.value &&
        bubble.value &&
        bubble.value.getBoundingClientRect().top < -100
      ) {
        context.emit("pop", props.idx);
        popped.value = true;
        bubble.value.style.display = "none";
      }
    }, 100);

    watch(popped, () => {
      if (popped.value) clearInterval(topPopper);
    });

    return {
      audio,
      bubble,
      size,
      pos,
      popped,
      playAudio,
      props,
    };
  },
};
</script>

<template>
  <div :class="`bubble-outer`">
    <audio ref="audio" class="audio">
      <source src="../assets/audio/poit.mp3" />
    </audio>
    <div
      :style="`width: ${size}px; height: ${size}px; left: ${pos}%`"
      ref="bubble"
      @click="playAudio"
      class="bubble floating"
    ></div>
  </div>
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
  cursor: pointer;
}

.bubble,
.bubble-outer {
  -webkit-tap-highlight-color: transparent;
}

.bubble:focus,
.bubble-outer:focus,
.audio:focus,
.audio:active {
  outline: none;
}

.floating {
  animation: float 12s forwards ease-in-out,
    sway 3s infinite ease-in-out alternate;
  -moz-animation: float 12s forwards ease-in-out,
    sway 3s infinite ease-in-out alternate;
  -webkit-animation: float 12s forwards ease-in-out,
    sway 3s infinite ease-in-out alternate;
}

@keyframes float {
  0% {
    top: 100%;
  }
  100% {
    top: -200px;
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
    transform: translateX(-25px);
  }
  100% {
    transform: translateX(25px);
  }
}

@-moz-keyframes sway {
  0% {
    transform: translateX(-25px);
  }
  100% {
    transform: translateX(25px);
  }
}

@-webkit-keyframes sway {
  0% {
    transform: translateX(-25px);
  }
  100% {
    transform: translateX(25px);
  }
}

.pop {
  animation: explode 0.05s forwards ease-out;
  -moz-animation: explode 0.05s forwards ease-out;
  -webkit-animation: explode 0.05s forwards ease-out;
}

@keyframes explode {
  0% {
    opacity: 1;
  }
  100% {
    transform: scale(1.3);
    opacity: 0;
  }
}

@-moz-keyframes explode {
  0% {
    opacity: 1;
  }
  100% {
    transform: scale(1.3);
    opacity: 0;
  }
}

@-webkit-keyframes explode {
  0% {
    opacity: 1;
  }
  100% {
    transform: scale(1.3);
    opacity: 0;
  }
}
</style>
