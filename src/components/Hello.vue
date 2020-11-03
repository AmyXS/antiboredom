<template>
  <div id="hello">
    <b-button variant="success" v-on:click="signalParentForClicked" >What to do?</b-button>
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