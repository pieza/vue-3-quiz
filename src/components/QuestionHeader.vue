<script setup>
import CompletionBar from './CompletionBar.vue'
import { defineProps } from "vue"

const { questionStatus, percent } = defineProps(['questionStatus', 'percent'])

</script>

<template>
  <div>
    <header>
      <h4>Question {{ questionStatus }}</h4>
      <CompletionBar :percent="percent" />
    </header>
  </div>
</template>

<style scoped>
header {
  margin-top: 20px;
}

header h4 {
  font-size: 30px;
}
</style>
