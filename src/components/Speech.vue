<template>
<button @click="sayWord">Say Word</button>
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
};
</script>

<style></style>
