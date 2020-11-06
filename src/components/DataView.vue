<template>
  <div id="dataview">
    <ul>
      <li v-for="item in items" :key="item.activity">
        {{ item.activity }}
      </li>
    </ul>

    <b-button v-if="items.length" v-on:click="whatElse" >What else?</b-button>
  </div>
</template>

<script>

export default {
  name: 'DataView',
  props: ['items'],
  methods: {
    whatElse: function () {
      this.$parent.getWhatToDo()
    }
  }
}
</script>