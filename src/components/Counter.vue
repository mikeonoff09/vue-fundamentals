/* eslint-disable */
<template>
  <div class="container">
    <h1>{{ customTitle }}</h1>
    <!-- The square() method gets called in each UI render -->
    <p>{{ counter }} <sup>2</sup> = {{ square() }}</p>
    <p>{{ counter }} <sup>2</sup> = {{ square() }}</p>
    <!-- The computedSquare Method stores the value in memory and rerenders only when
    there is a change in the properties or inside the method that would change
    the output, this avoids multiple recalculations and saves GPU... -->
    <p>{{ counter }} <sup>2</sup> = {{ computedSquare }}</p>
    <p>{{ counter }} <sup>2</sup> = {{ computedSquare }}</p>
    <p>{{ counter }} <sup>2</sup> = {{ computedSquare }}</p>
    <div>
      <button @click="increment">+ 1</button>
      <button @click="decrement">- 1</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Counter",
  props: {
    title: {
      type: String,
    },
    initialValue:{
      type: Number,
      // default: 0, // not necesary if adding required: true
      required: true, // if not provided it will throw an error
      validator: (value) => { // Use to perform validations
        return value >= 0; // drops a warning if false is returned
      },
    }
  },
  data() {
    return {
      counter: this.initialValue,
    };
  },
  methods: {
    square() {
      return this.counter * this.counter;
    },
    increment() {
      this.counter++;
    },
    decrement() {
      this.counter--;
    },
  },
  // This can be used in many places and it only gets called when there is a change
  // this is a better way to do it than the method above
  computed: {
    computedSquare() {
      return this.counter * this.counter;
    },
    customTitle() {
      return this.title || "Default Title";
    },
  },
};
</script>

<style>
.container {
  border: 1px solid #ccc;
  padding: 10px;
  margin: 10px;
}

button {
  background-color: #64b687;
  border-radius: 5px;
  border: 1px solid white;
  color: white;
  cursor: pointer;
  font-size: 1em;
  padding: 5px 15px;
  margin: 5px;
  height: 40px;
}

button:active {
  background-color: #5aaaab;
  transition-duration: 0.3s ease-in-out;
}
button:hover {
  background-color: #5aaaab;
  transition-duration: 0.3s ease-in-out;
}
</style>
