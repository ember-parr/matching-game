<template>
  <div>
    <h3>game on!</h3>
    <div class="matchingGame">
      <div v-for="card in CardData" :key="card.id" class="singleCard">
        <game-cards :card="card" @flip-card="flipCard" />
      </div>
    </div>
  </div>
</template>

<script>
import shuffle from "lodash.shuffle";
import { CardData } from "../assets/CardData.js";
import GameCards from "./GameCards.vue";
export default {
  components: { GameCards },
  data() {
    shuffle(CardData);
  }
};
</script>

<style scoped></style>
