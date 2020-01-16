<template>
  <g-link to="/" class="logo" title="Back to home">
    <transition name="theme">
      <div v-if="color == 'dark'">
        <g-image src="~/assets/img/logo-bright.svg" alt="logo" />
      </div>
    </transition>
    <transition name="theme">
      <div v-if="color == 'bright'">
        <g-image src="~/assets/img/logo-dark.svg" alt="logo" />
      </div>
    </transition>
  </g-link>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.dark .logo {
  animation: light-shadow-glow 3s 1;
  filter: invert(0) blur(0) drop-shadow(0 0 6px #000);
}

.bright .logo {
  animation: dark-shadow-glow 2s 1;
  filter: blur(0) drop-shadow(0 0 0 #000);
}

.logo {
  height: 67px;
  display: block;
  transition: color .15s ease-in-out;
  color: $textBright;
  position: relative;
  perspective: 200px;

  div {
    height: 67px;
    position: absolute;
    top: 0;
    left: 0;
  }

  img {
    height: 100%;
    width: auto;
  }
}

.theme-enter-active, .theme-leave-active {
  transition: opacity .15s ease-in-out;
}
.theme-enter, .theme-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

@keyframes light-shadow-glow {
  0% {
    filter: invert(1) blur(1.5rem) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000);
    opacity: 0;
  }

  45% {
    filter: invert(1) blur(0) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000);
    opacity: 0.65;
  }

  90% {
    filter: invert(0) blur(0) drop-shadow(0 0 2px #fff) drop-shadow(0 0 3px #fff) drop-shadow(0 0 4px #0ec604) drop-shadow(0 0 16px #0ec604);
  }

  100% {
    filter: invert(0) blur(0) drop-shadow(0 0 6px #000);
  }
}

@keyframes dark-shadow-glow {
  0% {
    filter: blur(1.5rem) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000) drop-shadow(0 0 0px #000);
    opacity: 0;
  }

  100% {
    filter: blur(0) drop-shadow(0 0 0 #000);
    opacity: 1;
  }
}
</style>


