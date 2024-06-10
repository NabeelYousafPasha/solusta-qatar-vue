<script setup>
import { ref } from 'vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { useForm } from "@inertiajs/vue3";

const form = useForm({
});

defineProps({
    tableData: Array,
    headerColumns: Array,
});

const selectedRow = ref(null);
const filters = ref([]);

const loadMore = () => {
    // leaving logic for later
};

const applyFilter = (filter) => {
    // Filter logic
    // leaving logic for later
};

const clearFilters = () => {
    filters.value = [];
    // Clear filter logic
    // leaving logic for later
};

const sortBy = (column) => {
    // Sorting logic
    // leaving logic for later
};

const selectRow = (row) => {
    selectedRow.value = row;
};

const showActions = () => {
    // leaving logic for later
};

const editRow = (row, column) => {
    // Inline editing logic
};

</script>

<template>
    <div>
        <v-container>
            <v-row>
                <v-col>
                    <div class="table-filters">
                        <!-- Filters -->
                        <input
                            v-for="filter in filters"
                            :key="filter"
                            type="text"
                            :id="filter"
                            :value="filter"
                            class="mt-1 block w-full"
                            @input="applyFilter(filter)"
                        />
                        <PrimaryButton
                            class="ms-4"
                            @click="clearFilters"
                        >
                            Clear Filters
                        </PrimaryButton>
                    </div>
                </v-col>
            </v-row>

            <v-row>
                <v-col>
                    <v-data-table
                        :headers="headerColumns"
                        :items="tableData"
                        item-value="id"
                        class="elevation-1"
                        show-select
                        @click:row="selectRow"
                    >
                        <template v-slot:item.action="{ item }">
                            <v-btn
                                v-if="selectedRow && selectedRow.id === item.id"
                                icon
                                @click.stop="showActions(item)"
                            >
                                <v-icon>mdi-dots-vertical</v-icon>
                            </v-btn>
                        </template>
                    </v-data-table>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<style scoped>

</style>
