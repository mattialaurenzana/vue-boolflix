<template>
    <div class="homepage">
        <h1>Popular film</h1>
        <div class="row">
            <div class="card" v-for="(film,index) in mostPopular" :key="index">
                <div class="img-container">
                    <img :src="firstImgPart+film.poster_path">
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
        <h1>Top rated film</h1>
        <div class="row">
            <div class="card" v-for="(film,index) in topRated" :key="index">
                <div class="img-container">
                    <img :src="firstImgPart+film.poster_path">
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
    
        props: {
            mostPopular: Array,
            topRated: Array,
        },
        data(){
            return{
                firstImgPart: "https://image.tmdb.org/t/p/w500",
                stars: [],
            }
        },
        methods:{
             checkTitle(originaltitle,title){
            if(originaltitle != title){
                return true;
            }
           
        }
        },
        computed: {
                  getStars(){

                 this.mostPopular.forEach((item)=>{
                    const array = [];
                     for(let i=0; i < (Math.ceil(item.vote_average / 2)); i++){
                        array.push('star');
                }
                this.stars.push(array);
                
                })
                return this.stars;
               
            }
        }
}
</script>

<style lang="scss" scoped>
    @import '../style/homepage.scss'
</style>