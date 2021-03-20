<template>
  <div id="app">
    <div class="innerDiv">
      <h1>Really Difficult Spelling Test</h1>
      <div v-if="!testFinished">
        <h4>word status: {{ activeIndex + 1 }} of {{ questions.length }}</h4>
        <speech :word="questions[activeIndex].word" />
        <form @submit.prevent="handleSubmit">
          <input
            type="text"
            spellcheck="false"
            v-model="userInput"
            placeholder="spell the word"
          />
          <div>
            <button type="submit" class="submit-btn">Submit</button>
          </div>
        </form>
      </div>

      <div v-else class="thisDiv">
        <score :questions="questions" />
        <answer-table :questions="questions" />
      </div>
    </div>
  </div>
</template>

<script>
import AnswerTable from "./components/AnswerTable.vue";
import Score from "./components/Score.vue";
import Speech from "./components/Speech";
import data from "./data";

export default {
  components: { Speech, Score, AnswerTable },
  data() {
    return {
      questions: data,
      activeIndex: 0,
      userInput: "",
    };
  },

  methods: {
    handleSubmit() {
      this.questions[this.activeIndex].userInput = this.userInput;
      this.activeIndex += 1;
      this.userInput = "";
    },
  },

  computed: {
    testFinished() {
      return this.questions.every((q) => q.userInput);
    },
  },
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
}
body {
  height: 100vh;
  background-color: rgb(249, 246, 211);
  background-image: url("https://i.pinimg.com/originals/63/7d/ea/637deafde69f6044b0fb63ca23872493.png");
  background-position: center;
  background-size: 100%;
  background-repeat: no-repeat;
  font-family: "Michroma", sans-serif;
}
.innerDiv {
  background-color: rgb(247, 223, 127);
  border: black 1px solid;
  border-radius: 10px;
  width: 75%;
  align-self: center;
  padding-top: 20px;
  padding-bottom: 60px;
  max-height: 90vh;
  overflow: auto;
}
input {
  border-radius: 10px;
  margin: 5px;
  text-align: center;
  width: 300px;
  font-size: 1.75rem;
  background-color: rgb(247, 237, 168);
}
.submit-btn {
  color: #000000;
  background-color: transparent;
  border: 2px solid #000000;
  border-radius: 5px;
  text-transform: uppercase;
  margin-top: 8px;
  padding: 5px;
}
</style>
