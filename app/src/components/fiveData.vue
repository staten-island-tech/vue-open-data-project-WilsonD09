<template>
  <div class="card">
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
