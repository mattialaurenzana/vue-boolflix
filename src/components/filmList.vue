<template>
  <div>
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
                        <i class="fas fa-star" v-for="(star,index) in stars[index]" :key="index"></i>
                    </div>
                </div>
            </div>
        </div>
  </div>
</template>

<script>
export default {

    data(){
        return{
            firstImgPart: "https://image.tmdb.org/t/p/w500",
              stars : [],
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
         getStars(){
            this.listFilm.forEach((item)=>{
                 const array = [];
                for(let i=0; i < (Math.ceil(item.vote_average / 2)); i++){
                    array.push('star');
                }
                this.stars.push(array);
                })
            }
     
    
    },
    mounted(){
           this.getStars()
        
        }
    }
  

</script>

<style lang="scss" scoped>
    @import '../style/filmList.scss'
</style>