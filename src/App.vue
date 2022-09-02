<template>
  <div id="app">

    <MyHeader @search="searching"/>
    <MyMain :filmList="filmList" :serieTv="serieTv"/>

  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';
import axios from "axios"

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
 
  },
  data(){
    return{
      filmList: [],
      serieTv:[]
    }
  },
  
  methods:{
    searching(searchedText){
      axios.get("https://api.themoviedb.org/3"+ "/search/movie?api_key=9ac8239a13b40749534dae9c92f8126a&language=it-IT"+"&query="+searchedText)
      .then(risultato=>{
        this.filmList=risultato.data.results;
      });
      axios.get("https://api.themoviedb.org/3"+"/search/tv?api_key=9ac8239a13b40749534dae9c92f8126a&language=it-IT"+"&query="+searchedText)
      .then(result =>{
        this.serieTv=result.data.results;
      })
    }
  }
}
</script>

<style lang="scss">
  html{
    background-color: #171717;
  }
</style>
