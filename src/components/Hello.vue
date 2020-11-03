<template>
  <div id="hello">
    <b-button variant="success" v-on:click="getWhatToDo" >What to do?</b-button>
    <ul>
      <li v-for="item in items" :key="item.activity">
        {{ item.activity }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Hello',
  data() {
    return {
        items: [
          { activity: "Do nothing", type: "social", price: "0", participants: 2 }
        ]
    };
    
  },
  methods: {
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
        console.log(newItem)
        this.$data.items.push(newItem)
      })
      .catch(e => {
        this.errors.push(e)
      })
    }
  }
}
</script>