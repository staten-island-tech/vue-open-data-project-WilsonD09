<template>
  <div class="flex flex-wrap justify-between">
    <fiveTrees v-for="(tree, index) in fiveData" :key="tree.status" :tree="tree" :id="index" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import fiveTrees from '@/components/fiveData.vue'
import { fiveSpecies } from '@/components/fiveSpecies'
const fiveData = ref('')
async function getData5() {
  let response = await fetch('https://data.cityofnewyork.us/resource/29bw-z7pj.json?$limit=1000')
  let data = await response.json()
  fiveData.value = data
  //return data
}
async function filterdata() {
  const data = await getData5()
  console.log(data)
  fiveData.value = data.filter((item) => item.status === 'Poor')
  console.log(fiveData.value)
}
onMounted(() => {
  getData5()
})
console.log(fiveSpecies)
</script>

<style scoped></style>
