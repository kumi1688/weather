<template>
    <v-container class="container">
        <v-row>
            <weather-card/>
        </v-row>
    </v-container>
</template>

<script>
    import axios from 'axios';

    import WeatherCard from "./WeatherCard";
    export default {
        name: "WeatherDataContainer",
        components:{
            "weather-card": WeatherCard,
        },
        data(){
            return{
                arr: new Array(5),
                weatherData: null,
            }
        },
        created() {
          this.getData();
        },
        methods:{
            async getData(){
                console.log(this.getUrl());
                axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*';
                axios.defaults.headers['Access-Control-Allow-Origin'] = '*';
                const result = await axios.get(this.getUrl());
                console.log(result);
            },
            getUrl(){
                let queryParams = "?" + encodeURIComponent("ServiceKey") + "=fQQmInPFuI3k1pbQjX1BaCfOE6zFzNXa9hXAEs92vl6OI140GB%2BGkwowNuF0YyKuRNTRFy%2F5BWAZb7N0ZfDuUw%3D%3D";
                queryParams += "&" + encodeURIComponent("ServiceKey") + "=" + encodeURIComponent("fQQmInPFuI3k1pbQjX1BaCfOE6zFzNXa9hXAEs92vl6OI140GB%2BGkwowNuF0YyKuRNTRFy%2F5BWAZb7N0ZfDuUw%3D%3D");
                queryParams += "&" + encodeURIComponent("pageNo") + "=" + encodeURIComponent("1");
                queryParams += "&" + encodeURIComponent("numOfRows") + "=" + encodeURIComponent("10");
                queryParams += "&" + encodeURIComponent("dataType") + "=" + encodeURIComponent("JSON");
                queryParams += "&" + encodeURIComponent("base_date") + "=" + encodeURIComponent("20200227");
                queryParams += "&" + encodeURIComponent("base_time") + "=" + encodeURIComponent("1100");
                queryParams += "&" + encodeURIComponent("nx") + "=" + encodeURIComponent("61");
                queryParams += "&" + encodeURIComponent("ny") + "=" + encodeURIComponent("120");
                return queryParams;
            }
        }
    }
</script>

<style scoped>
    .container{
        position: fixed; left: 0px;
        margin-top: 70px;
    }
</style>
