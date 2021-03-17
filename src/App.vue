<template>
  <div id="app">
    <speech :word="questions[activeIndex].word" />
    <form @submit.prevent="handleSubmit">
      <input
        type="text"
        spellcheck="false"
        v-model="userInput"
        placeholder="spell the word"
      />
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
import Speech from './components/Speech';
import data from "./data";

export default {
  components: { Speech },
  data() {
    return {
      questions: data,
      activeIndex: 0,
      userInput: "",
    };
  },
  
  methods: {
    handleSubmit() {
      console.log(this.userInput)
    }
  }
};
</script>

<style></style>
