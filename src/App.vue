<template>
  <div id="app" class="p-5" style="min-height:100vh" >
    <div id="logo" class="mb-5">
      <a href="https://github.com/AmyXS/antiboredom">
        <img id="logoImage" alt="Antiboredom logo" src="./assets/logo-dark.svg">
      </a>
    </div>

    <div id="welcome" v-if="!items.length">
      <Hello v-on:signalParentForClicked="onHelloClicked"/>
    </div>

    <div id="mainPage" v-if="items.length" class="mb-5">
      <b-container>
        <b-row>
          <b-col sm="2" class="mb-3">
            <Sidebar v-on:filterTypeChanged="onFilterTypeChanged" v-on:sortByPriceChanged="onSortByPriceChanged"/>
          </b-col>
          <b-col lg>
          <DataView :items="items" :filter_by_type="filter_by_type" :sort_by_price="sort_by_price"/>
          </b-col>
        </b-row>
      </b-container>
    </div>

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
        numItemsToFetch: 9
    };
  },
  methods: {
    onHelloClicked() {
      this.getWhatToDoTableData();
    },
    onFilterTypeChanged(filter_by_type) {
      this.filter_by_type = filter_by_type;
      console.log('Filter by type changed: ' + filter_by_type);
    },
    onSortByPriceChanged(sort_by_price) {
      this.sort_by_price = sort_by_price;
      console.log('Sort by price changed: ' + sort_by_price);
    },
    // Check if item is a duplicate of an existing item
    // Can't simply use includes() because each item also has an ID
    itemExists(item) {
      for (var i = 0; i < this.items.length; i++) {
        if(item.activity == this.items[i].activity) {
          return true;
        }
      }
      return false;
    },
    getWhatToDoTableData() {
      this.items = [];

      for (var i = 0; i < this.numItemsToFetch; i++) {
        this.getWhatToDo();
      }
    },
    getWhatToDo() {
      axios.get(`https://www.boredapi.com/api/activity/`)
      .then(response => {
        var newItem = {
          activity: response.data.activity,
          type: response.data.type,
          price: response.data.price,
          accessibility: response.data.accessibility,
          participants: response.data.participants,
        }
        if (!this.itemExists(newItem)) {
          newItem["id"] = this.items.length;
          this.items.push(newItem);
        }
      })
      .catch(e => {
        this.errors.push(e);
      })
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Bitter:ital@1&display=swap');
#logoImage {
  max-width: 100%;
  height: auto;
}
#app {
  font-family: 'Bitter', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #241B02;
  background-color: #241B02;
}
</style>
