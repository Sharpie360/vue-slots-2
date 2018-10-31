<template>
  <div id="app" class="container">
    <img width="25%" src="./assets/logo.png">
    <app-learn-slot class="mb-3">
      <h2 slot="first">Learning Slots</h2>
      <p>the learning curve is slight</p>
      <span slot="action" class="display-4">{{ actionText }}</span>
    </app-learn-slot>
    <input type="text" id="userTextInput" v-model="actionText" placeholder="type some text here">
    <button class="btn btn-primary mt-3 mr-3" @click="uppercaseText">Uppercase Text</button>
    <button class="btn btn-primary mt-3" @click="lowercaseText">Lowercase Text</button>
  </div>
</template>

<script>
import LearnSlot from "./components/LearnSlot";
export default {
  name: "App",
  data() {
    return {
      actionText: ""
    };
  },
  components: {
    "app-learn-slot": LearnSlot
  },
  methods: {
    uppercaseText(){
      this.actionText = this.actionText.toUpperCase()
    },
    lowercaseText(){
      this.actionText = this.actionText.toLowerCase()
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#userTextInput {
  display: block;
  margin: 0 auto;
}
</style>
