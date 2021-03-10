<template>
  <div id="app">
    <img
      alt="Game Hero Image"
      src="./assets/matching-hero_image.jpg"
      class="hero-image"
    />
    <div>
      <matching-game />
    </div>
  </div>
</template>

<script>
import MatchingGame from "./components/MatchingGame.vue";
export default {
  name: "App",
  components: {
    MatchingGame
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}
.hero-image {
  width: 100%;
  height: auto;
  min-width: 300px;
  max-width: 1000px;
}
</style>
