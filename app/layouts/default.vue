<template>
    <div class="min-h-screen">
        <header class="border-b">
            <nav class="mx-auto max-w-6xl px-4 py-6 flex gap-6">
                <NuxtLink to="/" class="font-semibold">Home</NuxtLink>
                <NuxtLink to="/about">About</NuxtLink>
                <NuxtLink to="/contact">Contact</NuxtLink>
                <NuxtLink to="/beliefs">Beliefs</NuxtLink>
                <NuxtLink to="/departments">Departments</NuxtLink>
                <NuxtLink to="/events">Events</NuxtLink>
                <NuxtLink to="/announcements">Announcements</NuxtLink>
            </nav>
        </header>
        <main class="mx-auto max-w-6xl px-4 py-10">
            <slot></slot>
        </main>

        <footer class="border-t mt-16">
            <div class="mx-auto max-w-6xl px-4 py-8 text-sm opacity-80">
                © {{ new Date().getFullYear() }} Westridge Baptist Church. All rights reserved.
            </div>
        </footer>
    </div>
</template>