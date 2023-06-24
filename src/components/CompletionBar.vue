<script setup>
import { defineProps } from "vue"

const { percent } = defineProps({
  percent: {
    default: 0
  }
})
</script>

<template>
  <div class="bar">
    <div class="completion" :style="{ width: `${percent}%` }"></div>
  </div>
</template>

<style scoped>
.bar {
  width: 300px;
  height: 50px;
  border: 3px solid bisque;
}

.completion {
  height: 100%;
  background-color: bisque;
}
</style>
