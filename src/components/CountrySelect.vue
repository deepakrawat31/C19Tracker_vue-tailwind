<script>
export default {
    name:'CountrySelect',
    props: ['countries'],
    data() {
        return {
            selected: 0,
        }
    },
    methods: {
        onChange() {
            const country = this.countries.find((item) => item.ID === this.selected);

            this.$emit('get-country', country);
        }
    }
}
</script>

<template>
    <select v-model="selected" @change="onChange" class="form-select mt-6 block w-full border p-2 rounded text-blue-700 bg-slate-500 bg-opacity-10">
        <option value="0" class="bg-slate-800">Select Country</option>
        <option v-for="country in countries" :value="country.ID" class="bg-slate-800">{{ country.Country }}</option>
    </select>
</template>