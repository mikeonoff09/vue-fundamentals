<template>
  <img alt="bg" :src="img" />
  <div class="bg-dark"></div>
  <div class="indecision-container">
    <input v-model="question" type="text" placeholder="Hazme una pregunta" />
    <div>Recuerda terminar con un signo de interrogación (?)</div>
    <div v-if="isValidQuestion">
      <h2>{{ question }}</h2>
      <h1>{{ answer }}</h1>
    </div>
  </div>
</template>
<script>
import { setTransitionHooks } from "vue";

export default {
  data() {
    return {
      question: "Seré millonario?",
      answer: null,
      img: null,
      isValidQuestion: false,
    };
  },
  watch: {
    question(value, oldValue) {
      this.isValidQuestion = false;
      if (!value.endsWith("?")) return;
      this.isValidQuestion = true;

      //   this.question = this.message;
      console.log(this.question);
      this.getAnswer();
    },
    answer(value, oldValue) {},
  },
  methods: {
    async getAnswer() {
      this.answer = "Pensando...";
      const { answer, image } = await fetch("https://yesno.wtf/api").then(
        (res) => res.json()
      );
      this.answer =
        answer === "yes" ? "Sí!" : answer === "no" ? "No!" : "Tal vez!";
      // validation
      // Mientras menos líneas de código mejor
      // if(answer === "yes") {
      //     this.answer = "Sí!";
      // } else if(answer === "no") {
      //     this.answer = "No!";
      // } else {
      //     this.answer = "Tal vez!";
      // }
      this.img = image;
    },
    // onEnter should trigger the http call to the API
    // onEnter() {
    //     console.log("onEnter");
    //     this.isValidQuestion = false;
    //     // if (!value.endsWith("?")) return;
    //     this.isValidQuestion = true;

    //     //   this.question = this.message;
    //     console.log(this.question);
    //     this.getAnswer();
    // },
  },
  //   props: {
  //     message: {
  //       type: String,
  //       default: "Seré millonario?",
  //     },
  //   },
};
</script>

<style scoped>
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.indecision-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 0px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>
