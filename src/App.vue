<template>
  <div id="app">
      <header-box @search="createUrlFilm"/>
      <main-container :titlelists="filmsList"  v-if="showResults"/>
      <advertising-box v-if="!showResults"/>
  </div>
</template>

<script>
import headerBox from './components/headerBox.vue'
import mainContainer from './components/mainContainer.vue'
import axios from 'axios'
import advertisingBox from './components/advertisingBox.vue'

export default {
  name: 'App',
  components: {
    headerBox,
    mainContainer,
    advertisingBox,
  },
  data(){
    return{
      filmsList: [],
      urlFilm: "",
  
    }
  },
  methods: {

    createUrlFilm(inputResearch){
      let string = "";
      string += "https://api.themoviedb.org/3/search/movie/";
      string += "?query="+inputResearch.toLowerCase();
      string += "&api_key=89f7b6916ed41033676697af1254857e"
      this.urlFilm = string;
      this.getFilmsList();

    },
    getFilmsList(){
          axios.get(this.urlFilm).then((response) =>{
          this.filmsList = response.data.results; 
       })
    },
    
  },
  computed: {
        showResults(){
        if(this.filmsList.length != 0){
        return true;
      }else{
        return false;
      }
    }
  }
   
      
}
</script>

<style lang="scss">
  @import './style/main.scss'
</style>
