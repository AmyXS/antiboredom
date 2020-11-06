<template>
  <div id="dataview">

    <span v-for="(item, index) in items" :key="item.activity">
      <b-card
        v-bind:title=item.activity
        v-bind:img-src=getImageURL(index)
        img-alt="Image"
        img-top
        style="max-width: 20rem;"
        class="mb-2"
      >
        <b-card-text>
          Type: {{ item.type }}
          <br/>
          Accessibility: {{ item.accessibility }} 
          <br/>
          Participants: {{ item.participants }} 
        </b-card-text>
      </b-card>
    </span>

      

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
    },
    getImageURL: function (index) {
      var url ="https://placedog.net/500/280/?id=5" + index
      return url
    }
  }
}
</script>