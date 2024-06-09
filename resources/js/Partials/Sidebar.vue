<script>
import { ref } from 'vue';

export default {
    setup() {
        const isOpen = ref(false);
        const toggleSidebar = () => {
            isOpen.value = !isOpen.value;
        };

        return {
            isOpen,
            toggleSidebar,
        };
    },
};
</script>

<template>
    <div :class="{ 'sidebar-open': isOpen }" @click="toggleSidebar">
        <!-- Sidebar content -->
    </div>
</template>

<style scoped>
.sidebar-open {
    /* Sidebar styles */
}
</style>
