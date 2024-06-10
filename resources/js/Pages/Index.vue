<script setup>
import {Head} from "@inertiajs/vue3";
import Table from "@/Components/Custom/Table.vue";

// we can mcok data from MySQL via APIs
// but for Solusta, I'm using hardcoded
const demoTableData = [
    {
        id: 1,
        name: 'Nabeel',
        email: 'nabeelyousafpasha@gmail.com',
        gender: 'male',
        age: 27,
        contact: '+92 321 5031089',
    },
    {
        id: 2,
        name: 'Nabeel 2',
        email: 'nabeelyousafpasha@gmail.com',
        gender: 'male',
        age: 27,
        contact: '+92 321 5031089',
    },
    {
        id: 3,
        name: 'Nabeel 3',
        email: 'nabeelyousafpasha@gmail.com',
        gender: 'male',
        age: 27,
        contact: '+92 321 5031089',
    },
    {
        id: 4,
        name: 'Nabeel 4',
        email: 'nabeelyousafpasha@gmail.com',
        gender: 'male',
        age: 27,
        contact: '+92 321 5031089',
    },
    {
        id: 5,
        name: 'Nabeel 5',
        email: 'nabeelyousafpasha@gmail.com',
        gender: 'male',
        age: 27,
        contact: '+92 321 5031089',
    }
];

</script>

<template>
    <div>
        <Head title="Index" />

        <div class="content mt-1">
            <p>Page Content</p>

            <Table
                id="demo-table"
                :headerColumns="[
                    {value: 'id', text: 'Id',},
                    {value: 'name', text: 'Name',},
                    {value: 'email', text: 'Email Address',},
                    {value: 'gender', text: 'Gender',},
                    {value: 'age', text: 'Age',},
                    {value: 'contact', text: 'Contact',},
                    {value: 'action', text: 'Actions', sortable: false},
                ]"
                :tableData="demoTableData"
            ></Table>
        </div>
    </div>
</template>

<style scoped>

</style>
