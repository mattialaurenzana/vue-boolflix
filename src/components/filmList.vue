<template>
  <div class="film-container">
        <h1 v-if="showTitle()">Sezione Film</h1>
        <div class="row">  
            <div v-for="(film,index) in listFilm" :key="index" class="card">
                <div class="img-container">
                    <img :src="firstImgPart+film.poster_path" alt="">
                </div>
                <div class="film-data">
                    
                       <div>
                            <span>Titolo:</span>{{film.title}}
                        </div>
                    <div v-if="checkTitle(film.original_title,film.title)">
                        <span>Titolo originale:</span>{{film.original_title}}
                    </div>
                    <div>
                        <span>Lingua:</span>
                        <div class="flag-container">
                            <img :src="`/flags/${film.original_language}.png`">
                        </div>
                       
                    </div>
                    <div>
                        <span>Voto:</span>
                        <create-stars :film="film"/>

                    </div>
                    <div>
                        <span>Overview: </span>{{film.overview}}
                    </div>
                    
                </div>
            </div>
        </div>
  </div>
</template>

<script>
import createStars from './createStars.vue'
export default {

    components: {
        createStars,
    },

    data(){
        return{
            firstImgPart: "https://image.tmdb.org/t/p/w500",
        }
    },
    props: {
        listFilm: Array,
    },
     methods: {
        checkTitle(originaltitle,title){
            if(originaltitle != title){
                return true;
            }
           
        },
        showTitle(){
            if(this.listFilm.length != 0){
                return true;
            }else{
                return false;
            }
        },
   
        },

    
    }

  

</script>

<style lang="scss" scoped>
    @import '../style/filmList.scss'
</style>