<script>
export default {
    name: 'Boxes',
    props: ['stats',],
    methods: {
        numberseperator(x) {
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }
    }
}
</script>

<template>
    <div class="grid md:grid-cols-2 gap-4 p-4">
        <!-- Box 1 -->
        <div class="shadow-md bg-blue-600 bg-opacity-20 p-2 text-center rounded">
            <h3 class="text-2xl text-blue-700 font-bold mb-4">Cases</h3>

            <div class="text-xl mb-2">
                <span class="text-slate-300 font-bold">New: {{ numberseperator(stats.NewConfirmed) }}</span>
            </div>

            <div class="text-xl mb-2">
                <span class="text-slate-300 font-bold">Total: {{ numberseperator(stats.TotalConfirmed) }}</span>
            </div>
        </div>
        
        <!-- Box 2 -->
        <div class="shadow-md bg-blue-600 bg-opacity-10 p-2 text-center rounded">
            <h3 class="text-2xl text-blue-700 font-bold mb-4">Deaths</h3>

            <div class="text-xl mb-2">
                <span class="text-slate-300 font-bold">New: {{ numberseperator(stats.NewDeaths) }}</span>
            </div>

            <div class="text-xl mb-2">
                <span class="text-slate-300 font-bold">Total: {{ numberseperator(stats.TotalDeaths) }}</span>
            </div>
        </div>
    </div>
</template>