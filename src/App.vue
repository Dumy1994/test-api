<template>
  <div id="app">
    <!-- header  -->
    <header-component />
    <!-- main  -->
    <app-loader v-if="loading" />
    <main-component :items="info" @performSearch="search"/>
    <!-- footer  -->
    <footer-component />
  </div>
</template>

<script>
import axios from 'axios';
import FooterComponent from "./components/FooterComponent.vue";
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import AppLoader from './components/AppLoader.vue';

export default {
  name: "App",
  components: {
    MainComponent,
    HeaderComponent,
    FooterComponent,
    AppLoader,
  },
  data() {
    return {
      apiPath: "https://jsonplaceholder.typicode.com/comments?q=",
      info: [],
      arrayMySearch: [],
      show: true,
      loading:false,
    };
  },
  methods:{
    getInfo(queryParams){
      axios.get(this.apiPath + queryParams).then((res)=>{
        this.info = res.data;
        this.loading = false;
      }).catch((error)=>{
        console.log(error);
      })
    },
    search(text){
      this.loading = true;
       const queryParams = text;
        this.getInfo(queryParams);
    },
  }
};
</script>

<style lang="scss">

</style>
