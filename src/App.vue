<template>
  <div>
    <h1>Countries</h1>
    <div class="main-container">
      <country-select :countries='countries'></country-select>
      <country-detail :country='selectedCountry'></country-detail>
    </div>
  </div>
</template>

<script>
import CountrySelect from './components/CountrySelect.vue'
import CountryDetail from './components/CountryDetail.vue'
import {eventBus} from './main.js'

export default {
  name: 'App',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
mounted(){
  fetch('https://restcountries.eu/rest/v2/all')
  .then(res => res.json())
  .then(countries => this.countries = countries)

  eventBus.$on('country-selected', (country) => {
    this.selectedCountry = country;
  })
},
  components: {
    "country-select": CountrySelect,
    "country-detail": CountryDetail
  }
}
</script>

<style>
  .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
