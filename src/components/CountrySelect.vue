<template lang="html">
  <div>
    <h3>Pick a country</h3>
    <select @change="handleClick" v-model="selectedCountry">
      <option v-for="country in countries" :value="country">{{country.name}}</option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'country-select',
  data() {
    return {
    selectedCountry: null
    }
  },
  props: ['countries'],
  methods: {
    handleClick(){
      eventBus.$emit('country-selected', this.selectedCountry)
    }
  }
}
</script>


<style lang="css" scoped>
</style>
