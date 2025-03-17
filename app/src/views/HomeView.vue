<template>
  <div class="container flex flex-wrap justify-around m-auto">
    <h1>Tree</h1>
    <fifteenTrees
      v-for="(tree, index) in fifteenData"
      :key="tree.status"
      :tree="tree"
      :id="index"
    />
    <fiveTrees v-for="(tree, index) in fiveData" :key="tree.status" :tree="tree" :id="index" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import fiveTrees from '@/components/fiveData.vue'
import fifteenTrees from '@/components/fifteenData.vue'
const fiveData = ref('')
const fifteenData = ref('')
async function getData15() {
  let response = await fetch('https://data.cityofnewyork.us/resource/uvpi-gqnh.json/?$limit=1000')
  let data = await response.json()
  fifteenData.value = data
}
async function getData5() {
  let response = await fetch('https://data.cityofnewyork.us/resource/29bw-z7pj.json/?$limit=1000')
  let data = await response.json()
  fiveData.value = data
}
onMounted(() => {
  getData15()
  getData5()
})
</script>

<style scoped></style>
