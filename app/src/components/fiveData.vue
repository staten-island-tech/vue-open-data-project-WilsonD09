<template>
  <div
    class="card w-[11%] h-[8rem] border-[0.3rem] mx-[.8rem] border-black rounded-[1rem] flex flex-col justify-around text-center mt-[2rem]"
    :class="{
      'bg-red-300': tree.status === 'Dead',
    }"
  >
    <h1>{{ tree.spc_common }}</h1>
    <h2>{{ tree.status }}</h2>
    <h2>{{ tree.boroname }}</h2>
    <h3>{{ id + 1 }}</h3>
  </div>
</template>

<script setup>
import { fiveSpecies } from '@/components/fiveSpecies'
const props = defineProps({
  tree: Object,
  id: Number,
})

if (!fiveSpecies.includes(props.tree.spc_common)) {
  fiveSpecies.push(props.tree.spc_common)
}
</script>

<style scoped></style>
