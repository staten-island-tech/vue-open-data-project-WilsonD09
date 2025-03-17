<template>
  <div
    class="card w-[11%] h-[8rem] border-[0.3rem] border-black rounded-[1rem] flex flex-col justify-around text-center mt-[2rem]"
  >
    <h1>{{ tree.spc_common }}</h1>
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
