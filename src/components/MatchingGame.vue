<template>
  <div>
    <h3>game on!</h3>
    <div class="matchingGame">
      <div v-for="card in languages" :key="card.id" class="singleCard">
        <game-cards
          :card="card"
          :image="require(`../assets/cards/${card.image}`)"
          :guessOne="guessOne"
          :guessTwo="guessTwo"
          @card-clicked="handleCardClick"
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
  },
  methods: {
    handleCardClick(card) {
      // don't do anything if a third card is clicked
      if (this.guessOne && this.guessTwo) return;

      // if the same card is clicked 2x, dont do anything
      if (this.guessOne === card) return;

      // assign first guess
      if (this.guessOne === null) {
        this.guessOne = card;
        return;
      }

      if (this.guessTwo === null) {
        this.guessTwo = card;
      }

      const [cardOne, cardTwo] = this.getMatchingCards(card.name);

      if (this.guessOne.name === this.guessTwo.name) {
        cardOne.foundMatch = true;
        cardTwo.foundMatch = true;
        this.guessOne = null;
        this.guessTwo = null;
      } else {
        setTimeout(() => {
          this.guessOne = null;
          this.guessTwo = null;
        }, 2000);
      }
    },
    getMatchingCards(name) {
      return this.languages.filter(l => l.name === name);
    }
  }
};
</script>

<style scoped>
.matchingGame {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.singleCard {
  margin: 20px;
  width: 20%;
  min-height: 100px;
}
</style>
