<script setup>
import { ref, reactive, computed } from 'vue'
const persons = reactive([
  { name: 'John Doe', age: 25, email: 'john@doe.com' },
  { name: 'Jane Doe', age: 26, email: 'jane@doe.com' },
  { name: 'John Smith', age: 27, email: 'john@smith.com' },
  { name: 'Jane Smith', age: 28, email: 'jane@smith.com' }
])

const activeIndex = ref(0)

function getActivePerson() {
  return persons[activeIndex.value]
}
</script>

<template>
  <section class="mx-auto container text-left">
    <h1 class="text-2xl mb-10">Vue Form</h1>
    <p class="my-5">{{ persons }}</p>
    <div class="flex ">
      <div class="w-1/2">
        <p>{{ activeIndex }}</p>
        
        <p class="mb-10">
        <h2>Select a person</h2>
        <select name="person" id="person" v-model="activeIndex">
          <option v-for="(person, index) in persons" :key="index" :value="index">{{ person.name }}</option>
        </select>
        </p>
      </div>
      <div>
        <div>
          <input class="p-5 my-3" type="text" v-for="(v, k, i) in persons[activeIndex]" :key="i" :placeholder="k" v-model="persons[activeIndex][k]">
        </div>
      </div>
    </div>

  </section>
</template>
<style scoped></style>
