<template>
  <div id="app">
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
import data from "./data";

export default {
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
