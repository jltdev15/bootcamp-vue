<script setup>
import { computed, ref } from 'vue';
import { BLOG_DATA } from './data'

console.log(BLOG_DATA);

const tagColor = ((tag) => {
  if (tag === 'Tech') {
    return 'bg-blue-600'
  }
  if (tag === 'Pinia') {
    return 'bg-yellow-600'
  }
  if (tag === 'JavaScript') {
    return 'bg-red-600'
  }
  if (tag === 'Vue 3') {
    return 'bg-green-600'
  }
  if (tag === 'Template') {
    return 'bg-gray-500'
  }

})

</script>

<template>
  <div>
    <h1 class="text-center p-6 text-3xl font-bold">Vue 3 Component with props</h1>
    <div class=" max-w-5xl mx-auto">
      <h2 class="text-center text-3xl font-bold">My Blog</h2>
      <div class="flex flex-wrap gap-6 p-12 justify-between">
        <article v-for="data in BLOG_DATA" :key="data.id" class="w-3/12 shadow">
          <h3 class=" p-3 bg-green-600 text-gray-50 font-bold text-2xl">{{ data.title }}</h3>
          <p class="p-3">{{ data.description }}.</p>
          <div class="flex justify-between items-center p-3">
            <span class="text-gray-400 text-xs">{{ data.author }}</span>
            <p class="text-gray-400 text-xs text-right">{{ data.duration }} mins read</p>
          </div>
          <div class="flex  gap-3 bg-gray-400 text-gray-50 p-3">
            <p :class="tagColor(tag)" v-for="tag in data.category" :key="tag.id" class="inline-block p-2 rounded-2xl">
              {{
                tag
              }}</p>

          </div>

        </article>
      </div>
    </div>
  </div>
</template>