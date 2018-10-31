<template>
  <div id="app" class="container">
    <button class="btn btn-info" id="auto-convert-toggle" @click="toggleAutoConvert">Auto Convert</button>
    <app-learn-slot class="mb-3">
      <h1 slot="first">Learning Slots</h1>
      <p>the learning curve is slight</p>
    </app-learn-slot>
    <input type="text" id="userTextInput" v-model="actionText" placeholder="type some text here">

    <button class="btn btn-danger mt-3 mr-3" @click="showCharCode">Get Char Code</button>
    <button class="btn btn-primary mt-3 mr-3" @click="uppercaseText">Uppercase Text</button>
    <button class="btn btn-success mt-3 mr-3" @click="lowercaseText">Lowercase Text</button>
    <button class="btn btn-secondary mt-3" @click="clearData">Clear Data</button>
    <hr>
    <app-results-panel class="my-3">
      <span slot="result" class="display-4">{{ actionText }}</span>
    </app-results-panel>
    <hr>
    <app-char-code 
      :charCodeArr="charCodeArr" 
      :actionText="actionText"
      v-show="actionText"></app-char-code>
  </div>
</template>

<script>
import LearnSlot from "./components/LearnSlot";
import ResultsPanel from "./components/ResultsPanel";
import CharCode from './components/CharCode'
export default {
  name: "App",
  data() {
    return {
      actionText: "",
      charCodeArr: [],
      charCodeResult: '',
      autoConvert: false
    };
  },
  components: {
    "app-learn-slot": LearnSlot,
    "app-results-panel": ResultsPanel,
    "app-char-code": CharCode
  },
  watch: {
    actionText: function(){
      if(this.autoConvert){
        this.showCharCode()
      }
    }
  },
  methods: {
    uppercaseText(){
      this.actionText = this.actionText.toUpperCase()
    },
    lowercaseText(){
      this.actionText = this.actionText.toLowerCase()
    },
    showCharCode(){
      this.charCodeArr = []
      this.actionText.split('').forEach((ltr) => {
        this.charCodeArr.push(ltr.charCodeAt())
        console.log(this.charCodeArr)
        this.charCodeResult = this.charCodeArr
      })
    },
    clearData(){
      this.actionText = ''
      this.charCodeArr = []
    },
    toggleAutoConvert(){
      this.autoConvert = !this.autoConvert
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

#auto-convert-toggle {
  position: absolute;
  top: 1rem;
  right: 1rem;
}

#userTextInput {
  display: block;
  margin: 0 auto;
}
</style>
