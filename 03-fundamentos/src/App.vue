<template>
  <div>
    <!-- <Counter :start="20" title="Entraron" /> -->
    <Indecision />
  </div>
</template>

<script>
import Indecision from "./components/Indecision.vue";

export default {
  name: "App",
  components: {
    Indecision,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 5rem;
}
</style>
