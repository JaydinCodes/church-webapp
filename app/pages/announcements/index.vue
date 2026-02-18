<script setup lang="ts">
const { data } = await useAsyncData('announcements', () =>
  queryContent('announcements')
    .sort({ date: -1 })
    .find()
)
</script>

<template>
  <div class="space-y-6">
    <h1 class="text-2xl font-bold">Announcements</h1>
    <ul class="space-y-2">
      <li v-for="a in data" :key="a._path" class="p-4 rounded border">
        <NuxtLink :to="a._path" class="font-medium">{{ a.title }}</NuxtLink>
        <div class="text-sm opacity-70">{{ a.date }}</div>
      </li>
    </ul>
  </div>
</template>
