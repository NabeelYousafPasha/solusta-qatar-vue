<script setup>
import { ref } from 'vue';
import { Link } from "@inertiajs/vue3";
import PrimaryButton from "@/Components/PrimaryButton.vue";

const isSidebarOpen = ref(true);

const toggleSidebar = () => {
    isSidebarOpen.value = !isSidebarOpen.value;
};

const menuItems = [
    {
        name: 'Data List',
        route: route('index', 'page=data-list'),
        icon: '<i class="fa fa-data-list"></i>'
    },
    {
        name: 'Function',
        route: route('index', 'page=function'),
        icon: '<i class="fa fa-function"></i>'
    },
    {
        name: 'Session',
        route: route('index', 'page=session'),
        icon: '<i class="fa fa-session"></i>'
    },
    {
        name: 'Guests List',
        route: route('index', 'page=guest-list'),
        icon: '<i class="fa fa-guest-list"></i>'
    },
    {
        name: 'Emails List',
        route: route('index', 'page=email-list'),
        icon: '<i class="fa fa-email-list"></i>'
    }
];
</script>

<template>
    <div>
        <v-btn
            @click="toggleSidebar"
        >
            Solusta - Sidebar
        </v-btn>
        <div
            class="sidebar-content"
            :class="{ 'sidebar-open': isSidebarOpen, 'sidebar-closed': !isSidebarOpen }"
            @click="toggleSidebar"
        >
            <ul class="sidebar-menu">
            <template
                v-for="(menu, index) in menuItems"
                :key="index"
            >
                <li class="menu-item">
                    <Link
                        :href="menu.route"
                        class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                    >
                        <b>{{ menu.name }}</b>
                    </Link>
                </li>
            </template>
            </ul>
        </div>
    </div>
</template>

<style scoped>

.sidebar a {
    display: block;
    color: #000;
    padding: 16px;
    text-decoration: none;
}

.sidebar a.active {
    background-color: #04AA6D;
    color: white;
}

.sidebar a:hover:not(.active) {
    background-color: #555;
    color: white;
}

/* Style for open sidebar */
.sidebar-open {
    width: 250px; /* Adjust as needed */
    transition: all 0.3s ease;
}

/* Style for closed sidebar */
.sidebar-closed {
    width: 0;
    overflow: hidden;
    transition: all 0.3s ease;
}


</style>
