<template>
  <div>
    <img v-if="img" :src="img" alt="bg" />
    <div class="bg-dark"></div>
    <div class="indecision-container">
      <input type="text" placeholder="Hazme una pregunta" v-model="question" />
      <small>Recuerda terminar con un signo de interrogación (?)</small>

      <div v-if="isValidQuestion">
        <!-- <h2>{{ question }}</h2> -->
        <h1>{{ answer === "yes" ? "SI" : "NO" }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: null,
      answer: null,
      img: null,
      isValidQuestion: false,
    };
  },
  methods: {
    async getAnswer() {
      this.answer = "Pensando...";
      const { answer, image } = await fetch("https://yesno.wtf/api").then((res) => res.json());

      this.answer = answer;
      this.img = image;
    },
  },
  watch: {
    question(value, oldvalue) {
      this.isValidQuestion = false;
      if (!value.includes("?")) return;

      this.isValidQuestion = true;
      this.getAnswer();
    },
  },
};
</script>

<style scoped>
small {
  display: block;
}
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
  background-color: rgba(0, 0, 0, 0.4);
}
.indecision-container {
  position: relative;
  z-index: 99;
}
input {
  width: 100%;
  max-width: 20rem;
  padding: 1rem;
  border-radius: 0.5rem;
  border: none;
  margin-bottom: 1rem;
}
input:focus {
  outline: none;
}
h1 {
  margin-top: 150px;
}
</style>
