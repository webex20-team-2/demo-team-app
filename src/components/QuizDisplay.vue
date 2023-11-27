<template>
  <div class="app">
    <h2>Q. {{ quiz.text }}</h2>
    <img class="quiz-image" :src="quiz.image" alt="クイズタイトル" />
    <div id="container">
      <button
        v-for="(choice, index) in choices"
        :key="choice"
        v-on:click="$emit('showFeedback', index)"
      >
        {{ choice.text }}
      </button>
    </div>
    <div>{{ feedback }}</div>
    <button v-show="!isHiddenNextButton" v-on:click="$emit('showNextQuiz')">
      次の問題へ
    </button>
  </div>
</template>

<script>
export default {
  props: {
    choices: Array,
    feedback: String,
    quiz: Object,
    isHiddenNextButton: Boolean,
  },
}
</script>

<style>
.app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.quiz-image {
  height: 300px;
  width: 300px;
  object-fit: contain;
}

.container {
  display: flex;
  height: 2em;
  width: 300px;
  padding: 1em;
  justify-content: space-around;
}
</style>
