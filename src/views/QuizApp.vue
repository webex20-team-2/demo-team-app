<template>
  <h1>Vue クイズ</h1>
  <div class="app">
    <h2>Q. {{ quizzes[count].text }}</h2>
    <img
      class="quiz-image"
      v-bind:src="quizzes[count].image"
      alt="クイズタイトル"
    />
    <div class="container">
      <button
        v-for="(choice, i) in quizzes[count].choices"
        v-bind:key="i"
        v-on:click="choiced(choice)"
      >
        {{ choice.text }}
      </button>
    </div>
    <div>{{ feedback }}</div>
    <div v-if="isCorrect && count != max">
      <button v-on:click="correct()">次の問題</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      isCorrect: false,
      feedback: "",
      max: 2,
      quizzes: [
        {
          text: "この星の名前は何でしょう？",
          image: require("../assets/Ganymede.jpg"),
          choices: [
            {
              text: "ゴリアテ",
              isCorrect: false,
              feedback:
                "残念！ゴリアテは、旧約聖書に登場するダビデに石で殺される巨人だよ。",
            },
            {
              text: "ゼニガメ",
              isCorrect: false,
              feedback:
                "残念！ゼニガメは、クサガメまたはニホンイシガメの幼体だよ。",
            },
            {
              text: "ガニメデ",
              isCorrect: true,
              feedback: "正解！ガニメデは、木星の第三惑星だよ！",
            },
          ],
        },
        {
          text: "いま、何問目？",
          image: require("../assets/Two.jpeg"),
          choices: [
            {
              text: "１",
              isCorrect: false,
              feedback: "残念！ひとつ少ないよ。",
            },
            {
              text: "２",
              isCorrect: true,
              feedback: "正解！１でも３でもないよ！",
            },
            {
              text: "３",
              isCorrect: false,
              feedback: "残念！ひとつ多いよ。",
            },
          ],
        },
        {
          text: "この城の名前は？",
          image: require("../assets/Maruoka.png"),
          choices: [
            {
              text: "丸岡城",
              isCorrect: true,
              feedback: "正解！どこからどうみても丸岡城だね。",
            },
            {
              text: "丸亀城",
              isCorrect: true,
              feedback: "残念！どこからどうみても丸亀城ではないよ。",
            },
            {
              text: "丸子城",
              isCorrect: false,
              feedback: "残念！どこからどうみても丸子城ではないよ。",
            },
          ],
        },
      ],
    }
  },
  methods: {
    choiced(choice) {
      this.feedback = choice.feedback
      this.isCorrect = choice.isCorrect
    },
    correct() {
      this.count += 1
      this.isCorrect = false
      this.feedback = ""
    },
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
