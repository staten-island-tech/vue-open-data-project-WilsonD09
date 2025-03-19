<template>
  <div class="flex flex-wrap justify-between">
    <fifteenTrees
      v-for="(tree, index) in fifteenData"
      :key="tree.status"
      :tree="tree"
      :id="index"
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import fifteenTrees from '@/components/fifteenData.vue'
const fifteenData = ref('')
async function getData15() {
  let response = await fetch('https://data.cityofnewyork.us/resource/uvpi-gqnh.json/?$limit=1000')
  let data = await response.json()
  fifteenData.value = data
}
onMounted(() => {
  getData15()
})
</script>

<style scoped></style>
