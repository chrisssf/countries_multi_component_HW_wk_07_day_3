<template>
  <div>
    <h1>Countries</h1>
    <countries-select :countries='countries'></countries-select>
    <country-detail :country="selectedCountry"></country-detail>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import CountriesSelect from './components/CountriesSelect'
import CountryDetail from './components/CountryDetail'

export default {
  name: 'app',
  data() {
    return {
      countries: [],
      selectedCountry: {}
    }
  },
  mounted() {
    fetch('https://restcountries.eu/rest/v2/all')
    .then(countriesData => countriesData.json())
    .then(countries => this.countries = countries)

    eventBus.$on('selected-country', (country) => {
      this.selectedCountry = country
      
    })
  },
  components: {
    "countries-select": CountriesSelect,
    "country-detail": CountryDetail
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
