<template>
  <div id="app">
    <img alt="Antiboredom logo" src="./assets/logo.svg">
    <Hello v-on:signalParentForClicked="onHelloClicked"/>

    <b-container>
      <b-row>
        <b-col cols="2">
          <Sidebar v-on:filterTypeChanged="onFilterTypeChanged" v-on:sortByPriceChanged="onSortByPriceChanged"/>
        </b-col>
        <b-col cols="10">
         <DataView :items="items" :filter_by_type="filter_by_type" :sort_by_price="sort_by_price"/>
        </b-col>
      </b-row>
    </b-container>

  </div>
</template>

<script>
import Hello from './components/Hello.vue'
import DataView from './components/DataView.vue'
import Sidebar from './components/Sidebar.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Hello,
    DataView,
    Sidebar
  },
  data() {
    return {
        items: [],
        filter_by_type: [],
        sort_by_price: '',
        numTableDataItems: 9
    };
  },
  methods: {
    onHelloClicked() {
      this.getWhatToDoTableData()
    },
    onFilterTypeChanged(filter_by_type) {
      this.filter_by_type = filter_by_type
      console.log('Filter by type changed: ' + filter_by_type)
    },
    onSortByPriceChanged(sort_by_price) {
      this.sort_by_price = sort_by_price
      console.log('Sort by price changed: ' + sort_by_price)
    },
    getWhatToDoTableData: function () {
      this.items = [];
      for (var i = 0; i < this.numTableDataItems; i++) {
        this.getWhatToDo();
      }
    },
    getWhatToDo: function () {
        axios.get(`https://www.boredapi.com/api/activity/`)
      .then(response => {
        console.log(response.data)
        let newItem = {
          activity: response.data.activity,
          type: response.data.type,
          price: response.data.price,
          accessibility: response.data.accessibility,
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
