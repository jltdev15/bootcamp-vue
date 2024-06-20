<script setup>
import { ref, watch, watchEffect } from "vue"

const todoId = ref(1)
const data = ref(null)

watch(
  todoId,
  async () => {
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/posts/${todoId.value}`
    )
    // Side Effect
    data.value = await response.json()
  },
  { immediate: true }
)

watchEffect(async () => {
  const response = await fetch(
    `https://jsonplaceholder.typicode.com/posts/${todoId.value}`
  )
  data.value = await response.json()
})


</script>

<template>
  <div>
    <h1>Watch and WatchEffect Functions Demo</h1>
    <button @click="todoId++">Change ID</button>
    <p>{{ data }}</p>
  </div>
</template>

<style scoped>
h1 {
  padding: 24px;
  font-size: 1.6rem;
  text-align: center;
}
</style>
