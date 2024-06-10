<script setup>
import { ref, computed, onMounted } from 'vue';
import { Head, Link, router, usePage } from '@inertiajs/vue3';
import { useThemeStore } from '../stores/theme';

defineProps({
    title: String,
});

const themeStore = useThemeStore();
const theme = computed(() => themeStore.theme);

</script>

<template>
    <div class="template-layout">
        <Head v-if="title" :title="title" />

        <div :class="theme">
            <div id="nabvar">
                <nav>
                    <!-- Navigation bar here -->
                </nav>
            </div>
            <div id="sidebar">
                <aside>
                    <!-- Sidebar here -->
                </aside>
            </div>
            <main id="main-content">
                <slot></slot>
            </main>
        </div>
    </div>
</template>

<style scoped>
/* Light and dark mode styles */
.light {
    background-color: white;
    color: black;
}
.dark {
    background-color: black;
    color: white;
}
</style>
