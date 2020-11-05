<template>
  <div id="app">
    <img alt="Antiboredom logo" src="./assets/logo.svg">
    <Hello v-on:signalParentForClicked="onHelloClicked"/>
    <DataView/>
  </div>
</template>

<script>
import Hello from './components/Hello.vue'
import DataView from './components/DataView.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Hello,
    DataView
  },
  data() {
    return {
        items: [
        ]
    };
  },
  methods: {
    onHelloClicked() {
      console.log("hello clicked")
      this.getWhatToDo()
    },
    getWhatToDo: function () {
        axios.get(`https://www.boredapi.com/api/activity/`)
      .then(response => {
        console.log(response.data)
        let newItem = {
          activity: response.data.activity,
          type: response.data.type,
          price: response.data.price,
          participants: response.data.participants
        }
        this.$data.items.push(newItem)
      })
      .catch(e => {
        this.errors.push(e)
      })
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
