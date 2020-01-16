<template>
    <form>
        <select v-on:change="handleChange" v-model="selectedCountry">
            <option v-for="(country, index) in countries" :value="country" :key="index">{{ country.name }}</option>
        </select>
    </form>
</template>

<script>

import { eventBus } from '../main'

export default {
    name: 'countries-select',
    data() {
        return {
            "selectedCountry": {}
        }
    },
    props: ['countries'],
    methods: {
        handleChange(){
            eventBus.$emit('selected-country', this.selectedCountry)
        }
    }
}
</script>

<style>

</style>