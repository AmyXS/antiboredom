<template>
  <div>
    <b-form-group label="Sort by price">
      <b-form-radio v-model="sort_by" name="sort-by-price" value="Low to high">Low to high</b-form-radio>
      <b-form-radio v-model="sort_by" name="sort-by-price" value="High to low">High to low</b-form-radio>
    </b-form-group>

    <div class="mt-3">sort_by: <strong>{{ sort_by }}</strong></div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        sort_by: ''
      }
    }
  }
</script>