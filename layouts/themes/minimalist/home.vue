<template>
    <div>
        <nav class="mt-10 w-3/4 mx-auto">
            <h1 class="text-4xl font-bold">
                {{ title }}
            </h1>
        </nav>

        <MinimalistMenu />

        <main class="mt-10 w-3/4 mx-auto">
            <div class="mt-4 hero">
                {{ description }}
            </div>

            <div class="mt-10">
                <NuxtLink class="underline " to="/archives">
                    Read all posts
                </NuxtLink>
            </div>
        </main>
        <MinimalistFooter />
    </div>
</template>
<script setup lang="ts">
import MinimalistMenu from '~/components/MinimalistMenu.vue'
import MinimalistFooter from '~/components/MinimalistFooter.vue'

defineProps<{
    doc: unknown;
    docs: unknown;
    currentPage: number;
    total: number;
    category: string;
    tag: string;
}>()

const config = useAppConfig()
const title = config.name
const description = config.description
</script>
<style>
body {
    @apply bg-white dark:bg-slate-900 dark:text-white;
}

.hero {
    background-image: url('https://source.unsplash.com/random/1920x1080/?nature,water') ;
    min-height: 400px;
    width: 100%;
}
</style>