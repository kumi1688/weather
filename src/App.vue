<template>
  <v-app id="inspire">
    <side-bar v-bind:drawer="drawer"/>

    <v-app-bar app color="indigo" dark>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"/>
      <v-toolbar-title>오늘의 날씨</v-toolbar-title>
    </v-app-bar>

    <weather-data-container/>
  </v-app>
</template>

<script>
  import SideBar from "./components/SideBar";
  import WeatherDataContainer from "./components/WeatherDataContainer";

  export default {
    components:{
      'weather-data-container': WeatherDataContainer,
      'side-bar': SideBar,
    },
    props: {
      source: String,
    },
    data: () => ({
      drawer: null,
    }),
  }
</script>
