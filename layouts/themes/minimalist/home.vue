<template>
    <div class="dark:bg-gray-900 dark:text-white">
        <div class="lg:w-full  navbar">
            <div class="navbar--inner lg:mx-auto">

                <h1 class="text-1xl font-bold">
                    {{ title }}
                </h1>
                <MinimalistMenu />
            </div>
        </div>

        <main class="mt-10 w-full lg:mx-auto dark:bg-gray-900 dark:text-white">
            <div v-if="doc">
                <div class="text-center">

                </div>

                <ContentRenderer
                    id="nuxtContent"
                    :value="doc"
                    class="prose pt-6 text-sm md:text-xl dark:prose-invert"
                />
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
</script>
<style lang="scss">
.prose {
    a {
        @apply underline underline-offset-2 decoration-dotted;
    }

    h1 a,
    h2 a,
    h3 a,
    h4 a,
    h5 a,
    h6 a {
        @apply no-underline ;
    }
}
.navbar {
    background-color: crimson;
    color: white;
    &--inner {
        padding: 10px 20px;
        max-width: 1080px;
    }
}

main {
    max-width: 1080px;
}
</style>

<!-- <template>
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
                TEST!!!
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
</style> -->