<script setup>
import { ref, computed } from 'vue';
import { Head, Link, router } from '@inertiajs/vue3';
import { useThemeStore } from '../stores/theme';

defineProps({
    title: String,
});

const themeStore = useThemeStore();
const theme = computed(() => themeStore.theme);

</script>

<template>
    <div class="template-layout">
        <Head :title="title" />

        <div :class="theme">
            <nav>
                <!-- Navigation bar here -->
            </nav>
            <aside>
                <!-- Sidebar here -->
            </aside>
            <main>
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
