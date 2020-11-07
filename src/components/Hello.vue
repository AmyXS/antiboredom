<template>
  <div id="hello">
    <b-button id="helloBtn" variant="success" v-on:click="signalParentForClicked" >What to do?</b-button>
  </div>
</template>

<script>
export default {
  name: 'Hello',
  methods: {
    signalParentForClicked() {
      this.$emit('signalParentForClicked')
    }
  }
}
</script>

<style>
#helloBtn {
  background-color: #FFC20D;
  border: none;
  color: #241B02;
  padding: 8px 30px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  font-weight: bold;
}
</style>
