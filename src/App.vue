<template>
    <div id="app">
        <img alt="Vue logo" src="./assets/logo.png">
        <SampleOne msg="Welcome to Your Vue.js App"/>
        <Chart :data=loadData></Chart>
    </div>
</template>

<script>
    import SampleOne from './components/SampleOne.vue';
    import Chart from './components/Chart.vue';
    import * as d3 from 'd3';
    export default {
        name: 'app',
        components: {
            SampleOne,
            Chart
        },
        data() {
            return {
                loadData: {}
            };
        },
        mounted() {
            this.fetchData();
        },
        methods: {
            async fetchData() {
                let data = await d3.json("./sample.json");
                this.loadData = data;
            }
        }
    };
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
