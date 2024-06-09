<script>
import { ref } from 'vue';

export default {
    setup() {
        const columns = ref(['Column1', 'Column2', 'Column3']);
        const rows = ref([]);
        const selectedRow = ref(null);
        const filters = ref([]);

        const loadMore = () => {
            // Lazy loading logic
        };

        const applyFilter = (filter) => {
            // Filter logic
        };

        const clearFilters = () => {
            filters.value = [];
            // Clear filter logic
        };

        const sortBy = (column) => {
            // Sorting logic
        };

        const selectRow = (row) => {
            selectedRow.value = row;
        };

        const showActions = () => {
            // Show action menu logic
        };

        const editRow = (row, column) => {
            // Inline editing logic
        };

        return {
            columns,
            rows,
            selectedRow,
            filters,
            loadMore,
            applyFilter,
            clearFilters,
            sortBy,
            selectRow,
            showActions,
            editRow,
        };
    },
};
</script>

<template>
    <div>
        <div>
            <!-- Filters -->
            <input v-for="filter in filters" :key="filter" @input="applyFilter(filter)">
            <button @click="clearFilters">Clear Filters</button>
        </div>
        <table>
            <thead>
            <tr>
                <th v-for="column in columns" :key="column">
                    <span @click="sortBy(column)">{{ column }}</span>
                </th>
                <th></th> <!-- For action menu -->
            </tr>
            </thead>
            <tbody>
            <tr v-for="row in rows" :key="row.id" @click="selectRow(row)">
                <td v-for="column in columns" :key="column">
                    <span @click="editRow(row, column)">{{ row[column] }}</span>
                </td>
                <td>
                    <button v-if="selectedRow === row" @click="showActions">...</button>
                </td>
            </tr>
            </tbody>
        </table>
        <button @click="loadMore">Load More</button>
    </div>
</template>

<style scoped>

</style>
