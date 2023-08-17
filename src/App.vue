<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- Dont forget to use the component -->
  <!-- <Counter title="Hola Counter" :initialValue="34"/> -->
  <!-- <Counter /> -->

  <Indecisions />
</template>

<script>
// import Counter from "./components/Counter.vue";
import Indecisions from "./components/Indecisions.vue";

export default {
  name: "App",
  components: {
    // Counter,
    Indecisions,
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
