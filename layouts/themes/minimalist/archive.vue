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

        <main class="mt-10 w-3/4 mx-auto  dark:bg-gray-900 dark:text-white">
            <h1 class="text-3xl font-bold">
                Alle Blogs
            </h1>
            <section class="mt-10">
                <div v-for="article in docs" :key="article._path">
                    <NuxtLink class="text-blue-400 underline" :to="article._path">
                        {{ article.date }} - {{ article.title }}
                    </NuxtLink>
                </div>
            </section>
            <section class="mt-10">
                <MinimalistPaginationBar :total="total" :current-page="currentPage" />
            </section>
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
            <h1 class="text-3xl font-bold">
                All Posts
            </h1>
            <section class="mt-10">
                <div v-for="article in docs" :key="article._path">
                    <NuxtLink class="text-blue-400 underline" :to="article._path">
                        {{ article.date }} - {{ article.title }}
                    </NuxtLink>
                </div>
            </section>
            <section class="mt-10">
                <MinimalistPaginationBar :total="total" :current-page="currentPage" />
            </section>
        </main>
        <MinimalistFooter />
    </div>
</template>
<script setup lang="ts">
import MinimalistMenu from '~/components/MinimalistMenu.vue'
import MinimalistPaginationBar from '~/components/MinimalistPaginationBar.vue'
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
</script> -->