<script setup>
import { ref, reactive, computed } from 'vue'
const color = ref('')
const getStyle = computed(() => {
  return {
    backgroundColor: color.value,
  }
})
</script>

<template>
  <section class="mx-auto container">
    <h1 class="text-2xl mb-10">Vue Form</h1>
    <span v-show="color">Your Favorite Color: {{ color }}</span>
    <p>
      Your Favorite Color: <input class="p-5" v-model="color" />
    </p>
    <div class="w-32 h-32 mt-10" :style="getStyle"></div>
  </section>
</template>
<style scoped></style>
