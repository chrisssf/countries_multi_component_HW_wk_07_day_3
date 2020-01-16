<template>
  <div v-if="country" id="details">
      <h3>{{country.name}}</h3>
      <dl>
          <dt>Capital:</dt>
          <dd>{{country.capital}}</dd>

          <dt>Population:</dt>
          <dd>{{country.population}}</dd>

          <dt>Languages: </dt>
          <dd>
              <ul>
                 <li v-for="language in country.languages">{{language.name}}</li>
            </ul>
        </dd>

      </dl>
      <img :src="country.flag" alt="">
  </div>
</template>

<script>
export default {
    name: 'country-detail',
    props: ['country']
}
</script>

<style scoped>

img {
    width: 400px;
}

#details {
    border: 3px solid black;
    padding: 15px;
    margin: 20px;
    max-width: 560px;
}

</style>