<template>
  <div class="card">
    <h2>{{ air.status }}</h2>
    <h3>{{ id + 1 }}</h3>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  air: Object,
  id: Number,
})
</script>

<style scoped></style>
