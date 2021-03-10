<template>
  <div>
    <h3>game on!</h3>
    <div class="matchingGame">
      <div v-for="card in languages" :key="card.id" class="singleCard">
        <game-cards
          :card="card"
          :image="require(`../assets/cards/${card.image}`)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import { CardData } from "../assets/CardData.js";
import GameCards from "./GameCards.vue";
import shuffle from "lodash.shuffle";
export default {
  components: { GameCards },
  data() {
    return {
      languages: shuffle([...CardData]),
      guessOne: null,
      guessTwo: null
    };
  }
};
</script>

<style scoped>
.matchingGame {
  border: 2px solid green;
}
.singleCard {
  border: 2px solid blue;
}
</style>
