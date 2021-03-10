<template>
  <div>
    <transition name="fade">
      <span v-if="showImage || card.foundMatch === true" class="languageImage">
        <img :src="image" alt="playing card" />
      </span>
      <span v-if="!showImage" class="languageImage">
        <img
          src="../assets/matching-cardBack.jpg"
          alt="playing card"
          @click="cardClicked"
        />
      </span>
    </transition>
  </div>
</template>

<script>
export default {
  props: ["card", "image", "guessOne", "guessTwo"],
  data() {
    return {
      open: false
    };
  },
  methods: {
    cardClicked() {
      this.$emit("card-clicked", this.card);
    }
  },
  computed: {
    showImage() {
      return (
        this.card.foundMatch ||
        this.card === this.guessOne ||
        this.card === this.guessTwo
      );
    }
  }
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}
img {
  max-width: 100%;
}
</style>
