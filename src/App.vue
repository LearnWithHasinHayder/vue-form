<script setup>
import { ref, reactive, computed } from 'vue'
const saarcCountries = ref([
  {name:"Bangladesh",capital:"Dhaka"},
  {name:"Nepal",capital:"Kathmandu"},
  {name:"Bhutan",capital:"Thimphu"},
  {name:"Sri Lanka",capital:"Colombo"},
  {name:"India",capital:"New Delhi"},
  {name:"Pakistan",capital:"Islamabad"},
  {name:"Maldives",capital:"Male"}
])


const getCapitals = computed(()=>{
  let capitals = [];
  saarcCountries.value.forEach(country => {
    capitals.push(country.capital)
  })
  return capitals.sort(()=> Math.random() - 0.5);
})

const getScore = computed(()=>{
  let score = 0;
  saarcCountries.value.forEach(country => {
    if(country.answer === country.capital){
      score++;
    }
  })
  return score;
})

</script>

<template>
  <section class="mx-auto container text-left">
    <h1 class="text-2xl mb-10">Vue Form</h1>
    <p class="mb-10">{{ saarcCountries }}</p>
    <p>Your Score: {{ getScore }}</p>
    <div class="mb-5 mt-5" v-for="country in saarcCountries">
      <p>What is the capital of {{ country.name }}</p>
      <template v-for="capital in getCapitals"> 
      <input type="radio" :name="country.name"  :value="capital" v-model="country.answer" />
      <label class="ml-2 mr-2">{{ capital }}</label>
      </template>
    </div>
  </section>
</template>
<style scoped></style>
