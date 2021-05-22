<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <TraditionalVueComponent :sampleWords="sampleWords" />
  <CompositionVueComponent :sampleWords="sampleWords" />
</template>

<script>
import TraditionalVueComponent from "./components/TraditionalVueComponent.vue";
import CompositionVueComponent from "./components/CompositionVueComponent.vue";

export default {
  name: "App",
  data() {
    return {
      sampleWords: [
        "Car",
        "Motorcycle",
        "Band",
        "Television",
        "And",
        "Or",
        "Rock",
        "Pop",
        "Surf",
        "Google",
      ],
    };
  },
  components: {
    TraditionalVueComponent,
    CompositionVueComponent,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
