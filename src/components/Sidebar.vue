<template>
  <div>
    <div>
      <b-form-group label="Filter by type:">
        <b-form-checkbox-group
          v-model="filter_by_type"
          :options="filter_by_options"
          class="mb-3"
          value-field="type"
          text-field="name"
          :change="filterTypeChanged()"
        ></b-form-checkbox-group>
      </b-form-group>
  </div>
    
    <b-form-group label="Sort by price">
      <b-form-radio-group
        id="sort-by-price-radio-group"
        v-model="sort_by_price"
        :options="sort_by_price_options"
        name="sort-by-price-options"
        :change="sortByPriceChanged()"
      ></b-form-radio-group>
    </b-form-group>
  </div>
</template>

<script>
  export default {
    props: ['items'],
    data() {
      return {
        sort_by_price: '',
        sort_by_price_options: [
          { text: 'Low to high', value: 'lowToHigh' },
          { text: 'High to low', value: 'highToLow' }
        ],
        filter_by_type: [],
        filter_by_options: [
          { type: 'education', name: 'Education' },
          { type: 'recreational', name: 'Recreational' },
          { type: 'social', name: 'Social' },
          { type: 'diy', name: 'DIY' },
          { type: 'charity', name: 'Charity' },
          { type: 'cooking', name: 'Cooking' },
          { type: 'relaxation', name: 'Relaxation' },
          { type: 'music', name: 'Music' },
          { type: 'busywork', name: 'Busywork' }
        ]
      }
    },
    methods: {
      filterTypeChanged: function() {
        this.$emit('filterTypeChanged', this.filter_by_type)
      },
      sortByPriceChanged: function() {
        this.$emit('sortByPriceChanged', this.sort_by_price)
      }
    }
  }
</script>

