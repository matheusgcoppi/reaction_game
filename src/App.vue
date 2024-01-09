<template>
  <h1> Reaction timer </h1>
  <div v-if="show">
    <Block :start="start" v-on:close="toggleButton"></Block>
  </div>
  <Results :result="result" v-if="showResult"></Results>
  <button @click="clickButton" :class="{ 'disabled': isDisabled }" :disabled='isDisabled'>play</button>
</template>

<script>

import Block from "@/components/Block.vue";
import Results from "@/components/Results.vue";

export default {
  name: 'App',
  components: {Results, Block},
  data() {
    return {
      show: false,
      start: null,
      result: null,
      showResult: false,
      clickedButton: true,
    }
  },
  methods: {
    clickButton() {
      this.clickedButton = false
      this.showResult = false
      setTimeout(() => {
        this.start = Date.now()
        this.show = true
      }, Math.floor(Math.random() * 5000));
    },
    toggleButton(result) {
      this.show = !this.show
      this.result = result
      this.showResult = !this.showResult
      this.clickedButton = true
    }
  },
  computed: {
    isDisabled() {
      return !this.clickedButton
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  padding: 17px;
  width: 100px;
  font-size: 25px;
  background-color: green;
  border-radius: 10px;
  border: none;
  outline: none;
  color: white;
  cursor: pointer;
}

button.disabled {
  background-color: grey;
}
</style>
