<template>
  <div id="dataview">

    <b-container>
      <b-row align-h="center" >
        <span v-for="item in filteredItems" :key="item.activity" class="mb-3"> 
          <b-card
            border-variant="dark"
            v-bind:title=item.activity
            v-bind:img-src=getImageURL(item.id)
            img-alt="Image"
            img-top
            style="max-width: 16rem; text-align: left;"
            class="mr-3">
            <b-card-text>
              Type: {{ item.type }}
              <br/>
              Accessibility: {{ item.accessibility }} 
              <br/>
              Participants: {{ item.participants }} 
              <br/>
              Price: {{ item.price }} 
            </b-card-text>
          </b-card>
        </span>
      </b-row>
      <b-row align-h="center" class="mt-5">
        <b-button id="whatElseBtn" v-if="items.length" v-on:click="whatElse" >WHAT ELSE?</b-button>
      </b-row>
    </b-container>

    
  </div>
</template>

<script>

export default {
  name: 'DataView',
  props: ['items', 'filter_by_type', 'sort_by_price'],
  methods: {
    whatElse: function () {
      this.$parent.getWhatToDoTableData()
    },
    getImageURL: function (index) {
      var url ="https://placedog.net/500/280/?id=1" + index
      return url
    }
  },
  computed: {
    filteredItems: function () {
      var filtered_list = this.items.filter(item => {
          if (this.filter_by_type.includes(item.type)) {
            return true
          } else {
            return false
          }
        })
        
      if (this.sort_by_price === 'lowToHigh') {
          filtered_list.sort((a, b) => {
          return a.price - b.price
        })
      } else if (this.sort_by_price === 'highToLow') {
          filtered_list.sort((a, b) => {
          return b.price - a.price
        })
      } 

      return filtered_list
    }
  }
}
</script>


<style>
#whatElseBtn {
  background-color: #FFC20D;
  border: none;
  color: #241B02;
  padding: 10px 120px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 18px;
  font-weight: bold;
}
</style>
