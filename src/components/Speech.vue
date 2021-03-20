<template>
  <div @click="sayWord" class="clickable">
    <img src="../assets/talkingBee.png" alt="talkingBee" />
    <p>click to listen</p>
  </div>
</template>

<script>
export default {
  props: ["word"],

  methods: {
    sayWord() {
      const utterance = new SpeechSynthesisUtterance(this.word);
      speechSynthesis.speak(utterance);
    },
  },

  watch: {
    word() {
      this.sayWord();
    },
  },
};
</script>

<style scoped>
.clickable {
  cursor: pointer;
}
 p {
   margin-top: 0;
 }
img {
  height: 75px;
  transition: transform 2s;
}
img:hover {
  transform: rotateZ(360deg);
}
</style>
