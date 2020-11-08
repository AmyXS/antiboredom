<template>
  <div id="body">
    <b-container>
      <b-row align-v="center">
        <b-col class="mt-5">
          <div id="text" class="mb-3">
          <p>Dear god, my mate is so bored.. </p>
          </div>
          <b-button id="helloBtn" variant="success" v-on:click="signalParentForClicked" >WHAT CAN HE DO?</b-button>
          </b-col>
      </b-row>
    </b-container>

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
  padding: 10px 60px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  font-weight: bold;
}
#body {
  color: white;
  background-color: #241B02;
}

</style>
