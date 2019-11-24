
<template>
    <div>
    <div class="row">
        <div class="col-3">
            <q-card class="info-card">
                <q-card-section>
                    INFO
                </q-card-section>
            </q-card>
        </div>
        <div class="col-6">
            <header class="header">
                <div class="heading-primary">
                    <span class="heading-primary-main">{{this.header}}</span>
                    <span class="heading-primary-sub">{{this.message}}</span>
                </div>
            </header>
        <div>
            <q-card class="my-card">
                <q-card-section>
                    <div class="input-one">
                        <q-select
                            outlined
                            dense
                            options-dense
                            v-model="model"
                            :options="this.options"
                            label="Standard"
                        >
                        </q-select>
                    </div>
                </q-card-section>
                <q-card-section>
                    <q-timeline>
                        <div v-for="fruit in fruits" :key="fruit">
                            <q-timeline-entry
                                v-for="fruit in fruits" :key="fruit"
                                :title="fruit"
                            />
                        </div>
                    </q-timeline>
                </q-card-section>
                <ul>
                    <li v-for="fruit in fruits" :key="fruit">
                        {{ fruit }}
                    </li>
                </ul>
            </q-card>
        </div>
        </div>
    </div>
    </div>
</template>

<style lang="scss">
    @import "../../node_modules/@ag-grid-community/core/dist/styles/ag-grid.css";
    @import "../../node_modules/@ag-grid-community/core/dist/styles/ag-theme-balham.css";
</style>

<script lang="ts">
/* eslint-disable */
import Vue from 'vue'
import button from '../components/button.vue'
import { AgGridVue } from '@ag-grid-community/vue';
import {AllCommunityModules} from "@ag-grid-community/all-modules";

export default Vue.extend({
    data () {
        return {
            message: 'Please submit a request here',
            header: 'TRAVEL TRACKER',
            model: null,
            dummyData: ["one", "two", "three"],
            fruits: ['apple', 'bananas'],
            options: [1,2,3,4,5,6,7],
            columnDefs: null,
            rowData: [
                {make: 'Toyota', model: 'Celica', price: 35000},
                {make: 'Ford', model: 'Mondeo', price: 32000},
                {make: 'Porsche', model: 'Boxter', price: 72000}
            ],
            gridOptions: {
                onGridReady: () => { // part of API: grid will automaticall call this when ready
                    console.log('Grid ready')
                    console.log(this.gridOptions.api.sizeColumnsToFit()) // is this the right call?
                },
                headerHeight: 48
            },
            modules: AllCommunityModules
        }
    },

    components: {
        button,
        AgGridVue
    },
    beforeMount() {
        this.columnDefs = [
            {headerName: '!', field: 'make'},
            {headerName: 'Model A and Model B', field: 'model'},
            {headerName: 'Price Volume IIIIIIIIIIIII', field: 'price'},
            {headerName: 'Maketh Naketh Shaketh AAAAAAAAAAA', field: 'make'},
            {headerName: 'Model B Trench Gun XXXXXXXXXX', field: 'model'},
            {headerName: 'Price Is Right', field: 'price'}
        ];

        this.rowData = [
            {make: 'Toyota', model: 'Celica', price: 35000},
            {make: 'Ford', model: 'Mondeo', price: 32000},
            {make: 'Porsche', model: 'Boxter', price: 72000}
        ];
    }
})
</script>