<template>
  <h1>Vue クイズ</h1>
  <div class="app">
    <h2>Q. {{ "この星の名前は何でしょう？" }}</h2>
    <img class="quiz-image" src="../assets/Ganymede.jpg" alt="クイズタイトル" />
    <div id="container">
      <button v-on:click="cho1()">
        {{ choi1 }}
      </button>
      <button v-on:click="cho2()">
        {{ choi2 }}
      </button>
      <button v-on:click="cho3()">
        {{ choi3 }}
      </button>
    </div>
    <div>{{ ans }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      choi1: "ゴリアテ",
      choi2: "ゼニガメ",
      choi3: "ガニメデ",
      ans: "答え",
    }
  },
  methods: {
    cho1() {
      this.ans =
        "残念！ゴリアテは、旧約聖書に登場するダビデに石で殺される巨人だよ。"
    },
    cho2() {
      this.ans = "残念！ゼニガメは、クサガメまたはニホンイシガメの幼体だよ。"
    },
    cho3() {
      this.ans = "正解！ガニメデは、木星の第三惑星だよ！"
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
