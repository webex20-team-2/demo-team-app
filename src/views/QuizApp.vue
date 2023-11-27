<template>
  <QuizDisplay
    :quiz="currentQuiz"
    :choices="currentChoices"
    :feedback="currentFeedback"
    :isHiddenNextButton="isHiddenNextButton"
    v-on:showFeedback="showFeedback"
    v-on:showNextQuiz="showNextQuiz"
  ></QuizDisplay>
</template>

<script>
import QuizDisplay from "@/components/QuizDisplay.vue"
export default {
  components: { QuizDisplay },
  data() {
    return {
      quizIndex: 0,
      currentFeedback: "答え",
      isHiddenNextButton: true,
      quizzes: [
        {
          text: "この星の名前は何でしょう？",
          image: require("@/assets/Ganymede.jpg"),
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
          image: require("@/assets/Two.jpeg"),
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
          image: require("@/assets/maruoka.png"),
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
    showFeedback: function (choiceIndex) {
      const currentChoice = this.currentChoices[choiceIndex]
      this.currentFeedback = currentChoice.feedback
      if (this.quizIndex < 2) {
        this.isHiddenNextButton = !currentChoice.isCorrect
      }
    },
    showNextQuiz: function () {
      this.quizIndex++
      this.isHiddenNextButton = true
      this.currentFeedback = ""
    },
  },
  computed: {
    currentChoices: function () {
      return this.quizzes[this.quizIndex].choices
    },
    currentQuiz: function () {
      const quiz = this.quizzes[this.quizIndex]
      return {
        text: quiz.text,
        image: quiz.image,
      }
    },
  },
}
</script>
