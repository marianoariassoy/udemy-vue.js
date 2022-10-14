<template>
  <div>
    <h2>{{ customTitle }}</h2>
    <div>{{ counter }} <sup>2</sup> = {{ squareCounter }}</div>
    <button @click="increse">+1</button>
    <button @click="decrese">-1</button>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    start: {
      type: Number,
      default: 100,
      // required: true
      validator(value) {
        return value >= 0;
      },
    },
  },
  name: "Counter",
  data() {
    return {
      counter: this.start,
    };
  },
  methods: {
    increse() {
      this.counter++;
    },
    decrese() {
      this.counter--;
    },
  },
  computed: {
    squareCounter() {
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title || "Counter";
    },
  },
};
</script>

<style>
div {
  margin-bottom: 1rem;
}
button {
  margin: 5px;
  background-color: #42b883;
  color: black;
  border: black;
  font-size: 1rem;
  cursor: pointer;
  height: 3rem;
  aspect-ratio: 1;
  border-radius: 5px;
}
button:hover {
  background-color: #35495e;
  color: white;
}
</style>
