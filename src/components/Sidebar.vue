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
        ></b-form-checkbox-group>
      </b-form-group>
      <div class="mt-3">Filter by type: <strong>{{ filter_by_type }}</strong></div>
   
  </div>
    
    <b-form-group label="Sort by price">
      <b-form-radio-group
        id="sort-by-price-radio-group"
        v-model="sort_by"
        :options="sort_by_options"
        name="sort-by-price-options"
      ></b-form-radio-group>
    </b-form-group>

    <div class="mt-3">sort_by: <strong>{{ sort_by }}</strong></div>
  </div>
</template>

<script>
  export default {
    props: ['items'],
    data() {
      return {
        sort_by: '',
        sort_by_options: [
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
    }
  }
</script>

