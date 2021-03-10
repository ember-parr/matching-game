<template>
  <div @click="open = !open">
    <transition name="fade">
      <span v-if="open || card.foundMatch === true" class="languageImage">
        <img :src="image" alt="playing card" />
      </span>
      <span v-if="!open" class="languageImage">
        <img src="../assets/matching-cardBack.jpg" alt="playing card" />
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
