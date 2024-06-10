<script setup>
import { ref, computed, onMounted } from 'vue';
import { Head, Link, router, usePage } from '@inertiajs/vue3';
import { useThemeStore } from '../stores/theme';
import Sidebar from "@/Partials/Sidebar.vue";

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
            <div id="sidebar" class="sidebar">
                <aside>
                    <Sidebar />
                </aside>
            </div>
            <div id="main-content" class="main-content">
                <div id="nabvar">
                </div>
                <slot></slot>
            </div>
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

/* The side navigation menu */
.sidebar {
    margin: 0;
    padding: 0;
    width: 200px;
    background-color: #f1f1f1;
    position: fixed;
    height: 100%;
    overflow: auto;
}

/* Page content. The value of the margin-left property should match the value of the sidebar's width property */
div.main-content {
    margin-left: 200px;
    padding: 1px 16px;
    height: 1000px;
}

/* On screens that are less than 700px wide, make the sidebar into a topbar */
@media screen and (max-width: 700px) {
    .sidebar {
        width: 100%;
        height: auto;
        position: relative;
    }
    .sidebar a {float: left;}
    div.main-content {margin-left: 0;}
}

/* On screens that are less than 400px, display the bar vertically, instead of horizontally */
@media screen and (max-width: 400px) {
    .sidebar a {
        text-align: center;
        float: none;
    }
}
</style>
