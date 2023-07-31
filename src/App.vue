<script setup>
import { ref } from 'vue'
import { countries } from './data/countries.js'
const search = ref('') 

function getFilteredCountries() {
  return countries.filter(country => {
    return country.name.toLowerCase().startsWith(search.value.toLowerCase())
  })
}
</script>

<template>
  <section class="mx-auto container text-left">
    <h1 class="text-2xl mb-10">Vue Form</h1>
    <p class="my-5">{{ search }}</p>
    <p class="my-5">
      search: <input class="p-3" type="text" v-model="search" >
    </p>
    <p class="mt-10">
    <ul>
      <li v-for="country in getFilteredCountries()" :key="country.code">
        {{country.name}}
        <!-- <span class='text-red-500'>{{ search }}</span>{{country.name.toLowerCase().replace(search,'')}} -->
      </li>
    </ul>
    </p>


  </section>
</template>
<style scoped></style>
