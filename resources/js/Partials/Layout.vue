<script>
import { computed } from 'vue';
import { useThemeStore } from '../stores/theme';

export default {
    setup() {
        const themeStore = useThemeStore();
        const theme = computed(() => themeStore.theme);

        return {
            theme,
        };
    },
};
</script>

<template>
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
