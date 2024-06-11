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
    customFilters: Array,
    rowUniqueValue: String,
});

const selectedRow = ref(null);
const selectedFilters = ref([]);
const search = ref(null);

const loadMore = () => {
    // leaving logic for later
};

const applySeachFilter = (filter) => {
    // Filter logic
    // we can do axios call again, with query param of filter

    let ep = `axios call for solusta/api?q=${search.value}`;
    alert(ep);
};

const clearSearchFilter = () => {
    search.value = null;
    // Clear filter logic

    let ep = `axios call for solusta/api with any query params`;
    alert(ep);
};

const clearFilters = () => {
    selectedFilters.value = [];
    // Clear filter logic

    let ep = `axios call for solusta/api with any query params`;
    alert(ep);
};

const resetSearchAndFilters = () => {
    clearFilters();
    clearSearchFilter();
}

const toggleFilter = (filter) => {
    const index = selectedFilters.value.indexOf(filter);
    if (index === -1) {
        selectedFilters.value.push(filter); // Add filter if not already selected
    } else {
        selectedFilters.value.splice(index, 1); // Remove filter if already selected
    }

    let ep = `axios call for solusta/api with updated filters`;
    alert(ep);
}

const isSelectedFilter = (filter) => {
    return selectedFilters.value.includes(filter);
}

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
                    <v-chip
                        v-for="(filter, index) in customFilters"
                        :key="index"
                        @click="toggleFilter(filter)"
                        :color="isSelectedFilter(filter) ? 'primary' : ''"
                    >
                        {{ filter }}
                    </v-chip>
            </v-col>
            </v-row>

            <v-row>
                <v-col>
                    <div class="table-search-filter">
                        <!-- Filters -->
                        <v-text-field
                            v-model="search"
                            label="Search"
                            outlined
                            dense
                        ></v-text-field>

                        <v-btn
                            class="ms-4"
                            @click="applySeachFilter"
                        >
                            Search
                        </v-btn>

                        <v-btn
                            class="ms-4"
                            @click="resetSearchAndFilters"
                        >
                            Reset Search & Filters
                        </v-btn>
                    </div>
                </v-col>
            </v-row>

            <v-row>
                <v-col>
                    <v-data-table
                        :headers="headerColumns"
                        :items="tableData"
                        :item-value="rowUniqueValue"
                        class="elevation-1"
                        density="compact"
                        show-select
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

                        <!-- Column for inline editing -->
<!--                        <template #item.action="{ item }">-->
<!--                            <v-btn-->
<!--                                icon-->
<!--                                @click.stop="editRow(item)"-->
<!--                            >-->
<!--                                <v-icon>mdi-pencil</v-icon>-->
<!--                            </v-btn>-->
<!--                        </template>-->

                        <!-- Edit dialog -->
                        <template #item.selected="{ item }">
                            <v-dialog
                                v-model="editDialog"
                                max-width="500"
                            >
                                <v-card>
                                    <v-card-title>Edit Row</v-card-title>
                                    <v-card-text>
                                        <!-- Input fields for editing -->
                                        <v-text-field v-model="editedItem.name" label="Name"></v-text-field>
                                        <v-text-field v-model="editedItem.type" label="Type"></v-text-field>
                                        <!-- Add more input fields as needed -->
                                    </v-card-text>
                                    <v-card-actions>
                                        <v-btn color="primary" @click="saveRow">Save</v-btn>
                                        <v-btn color="error" @click="cancelEdit">Cancel</v-btn>
                                    </v-card-actions>
                                </v-card>
                            </v-dialog>
                        </template>
                    </v-data-table>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<style scoped>

</style>
