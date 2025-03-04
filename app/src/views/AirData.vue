<template>
  <div>
    <h2>{{ pokemon.name }}</h2>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'
const route = useRoute()
const airData = ref('')
async function getData() {
  let response = await fetch(`https://data.cityofnewyork.us/resource/dsyc-npkh.json`)
  let data = await response.json()
  airData.value = data
}

onMounted(() => {
  getData()
})
</script>

<style scoped></style>
