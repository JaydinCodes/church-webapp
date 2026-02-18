<script setup lang="ts">
const { data: pinnedAnnouncements } = await useAsyncData('pinned', () =>
  queryContent('announcements')
    .where({ pinned: true })
    .sort({ date: -1 })
    .limit(3)
    .find()
)

const { data: upcomingEvents } = await useAsyncData('home-events', () =>
  queryContent('events')
    .sort({ start: 1 })
    .limit(3)
    .find()
)
</script>

<template>
  <div class="space-y-10">
    <section class="space-y-3">
      <h1 class="text-3xl font-bold">Welcome</h1>
      <p class="opacity-80">
        Baptist church community — worship, teaching, fellowship, mission.
      </p>
      <div class="flex gap-3">
        <NuxtLink to="/contact" class="px-4 py-2 rounded bg-black text-white">Plan a Visit</NuxtLink>
        <NuxtLink to="/announcements" class="px-4 py-2 rounded border">View Announcements</NuxtLink>
      </div>
    </section>

    <section class="space-y-3">
      <h2 class="text-xl font-semibold">Pinned Announcements</h2>
      <ul class="space-y-2">
        <li v-for="a in pinnedAnnouncements" :key="a._path" class="p-4 rounded border">
          <NuxtLink :to="a._path" class="font-medium">{{ a.title }}</NuxtLink>
        </li>
      </ul>
    </section>

    <section class="space-y-3">
      <h2 class="text-xl font-semibold">Upcoming Events</h2>
      <ul class="space-y-2">
        <li v-for="e in upcomingEvents" :key="e._path" class="p-4 rounded border">
          <NuxtLink :to="e._path" class="font-medium">{{ e.title }}</NuxtLink>
          <div class="text-sm opacity-70">{{ e.location }}</div>
        </li>
      </ul>
    </section>
  </div>
</template>
