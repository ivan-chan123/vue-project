<template>
    <div>
        <q-select
            v-model="this.model"
            :options="this.options"
            label="Standard"
        />
    </div>
</template>

<script lang="ts">
/* eslint-disable */
import Vue from 'vue'
export default Vue.extend({
    name: 'button',
    data() {
        return {
            model: null,
            options: [1,2,3,4,5,6,7]
        }
    }

})
</script>