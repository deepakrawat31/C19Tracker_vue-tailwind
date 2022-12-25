<script>
import Data from './Data.vue'
import Boxes from './Boxes.vue'
import CountrySelect from './CountrySelect.vue'

export default {
    name: 'Main',
    components: {
        Data,
        Boxes,
        CountrySelect,
    },
    data() {
        return {
            loading: true,
            title: 'Global',
            dataDate: '',
            stats: {},
            countries: [],
            loadingImg: './src/assets/hourglass.gif',
        }
    },
    methods: {
        async fetchCovidData() {
            const res = await fetch('https://api.covid19api.com/summary');
            const data = await res.json();
            return data;
        },
        getCountryData(country) {
            this.stats = country;
            this.title = country.Country;
        },
        async clearCountryData() {
            this.loading = true;
            const data = await this.fetchCovidData();
            this.title = 'Global';
            this.stats = data.Global;
            this.loading = false;
        }
    },
    async created() {
        const data = await this.fetchCovidData();
        this.dataDate = data.Date;
        this.stats = data.Global;
        this.countries = data.Countries;
        this.loading = false;
    },
}
</script>

<template>
    <main v-if="!loading" class="p-5">
        <Data :country="title" :date="dataDate" />
        <CountrySelect @get-country="getCountryData" :countries="countries" />
        <Boxes :stats="stats" />
        <button v-if="stats.Country" @click="clearCountryData" class="bg-blue-900 text-slate-200 rounded p-2 mt-4 focus:outline-none hover:bg-blue-800">Clear Country</button>
    </main>
    <main v-else class="flex-col align-center justify-center text-center">
        <div class="text-blue-300 text-2xl mt-2 mb-3">
            Fetching Data
        </div>
        <img :src="loadingImg" class="w-40 m-auto" alt="hourglass">
    </main>
</template>