<template>
  <div id="app">
      <header-box @search="createUrlFilm"/>
      <main-container :titlelists="filmsList"/>
  </div>
</template>

<script>
import headerBox from './components/headerBox.vue'
import mainContainer from './components/mainContainer.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    headerBox,
    mainContainer
  },
  data(){
    return{
      filmsList: [],
      urlFilm: "",
    }
  },
  methods: {

    createUrlFilm(inputResearch){
      console.log('ciae');
      let string = "";
      string += "https://api.themoviedb.org/3/search/movie/";
      string += "?query="+inputResearch;
      string += "&api_key=89f7b6916ed41033676697af1254857e"
      this.urlFilm = string;
      this.getFilmsList();

    },
    getFilmsList(){
          console.log('ciaone');
          axios.get(this.urlFilm).then((response) =>{
          this.filmsList = response.data.results; 
       })
    }

   
  },
   
      
}
</script>

<style lang="scss">
  @import './style/main.scss'
</style>
