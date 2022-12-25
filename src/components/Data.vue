<script>
import moment from 'moment'

export default {
    name: 'Data',
    props: ['country', 'date'],
    computed: {
        timestamp: function() {
            return moment(this.date).format('MMMM Do YYYY, h:mm:ss a');
        } 
    }
}
</script>

<template>
    <div class="text-center">
        <h2 class="text-blue-400 text-2xl font-bold md:text-3xl">{{ country }}</h2>
        <div class="text-blue-400 text-xl mt-2 mb-2 md:text-2xl">
            {{ timestamp }}
        </div>
    </div>
</template>