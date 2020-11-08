<template>
  <div id="body">
    <b-container>
      <b-row class="text-center" align-v="center">
        <b-col>
          <div id="text" class="mb-2">
          <p>Dear god, my mate is so bored.. </p>
          </div>
          <b-button id="helloBtn" variant="success" v-on:click="signalParentForClicked" >What can he do?</b-button>
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
  padding: 10px 45px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  font-weight: bold;
}
#body {
  position: absolute;
    top: 400px; /* Header Height */
    bottom: 0px;
    width: 100%;
}

</style>
