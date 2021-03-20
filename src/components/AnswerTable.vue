<template>
  <div>
    <v-simple-table>
      <template>
        <thead>
          <tr>
            <th>Your Answers</th>
            <th>Correct Spellings</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="question in questions" :key="question.word">
            <td :class="{ wrong: question.userInput !== question.word }">{{ question.userInput }}</td>
            <td>{{ question.word }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
export default {
  props: ["questions"],

//   computed: {
//     misspelled() {
//       return console.log(this.questions.userInput !== this.questions.word)
//     },
//   },
};
</script>

<style scoped>
td,
th {
  border: 1px solid black;
  padding: 0.5em;
  font-size: 1.5rem;
  background-color: rgb(247, 237, 168);
  border-radius: 10px;
}
v-simple-table {
  border-spacing: 0.5rem;
}
.wrong {
  border: red 2px solid;
  color: red;
}
</style>
