<template>
  <div
    class="card w-[11%] h-[8rem] border-[0.3rem] mx-[.8rem] border-black rounded-[1rem] flex flex-col justify-between text-center mt-[2rem]"
    :class="{
      'bg-red-300': tree.status === 'Dead',
      'bg-green-300': tree.status === 'Alive',
      'bg-yellow-300': tree.status === 'Stump',
    }"
  >
    <h1>{{ tree.spc_common }}</h1>
    <h2>{{ tree.health }}</h2>
    <h2>{{ tree.status }}</h2>
    <h3>{{ id + 1 }}</h3>
  </div>
</template>

<script setup>
const props = defineProps({
  tree: Object,
  id: Number,
})
</script>

<style scoped></style>
