<template>
     <div>
         <h1 v-if="showTitle()">Sezione Serie TV</h1>
         <div class="row">
         
            <div v-for="(serie,index) in seriesList" :key="index" class="card">
                <div class="img-container">
                    <img :src="firstImgPart+serie.poster_path" alt="">
                </div>
                <div class="film-data">
                    <div>
                        <span>Titolo:</span>{{serie.name}}
                    </div>
                    <div v-if="checkTitle(serie.original_name,serie.name)">
                        <span>Titolo originale:</span>{{serie.original_name}}
                    </div>
                    <div>
                        <span>Lingua:</span>
                        <div class="flag-container">
                            <img :src="`/flags/${serie.original_language}.png`">
                        </div>
                       
                    </div>
                    <div>
                        <span>Voto:</span>
                        <i class="fas fa-star" v-for="(item,index) in stars[index]" :key="index"></i>
                    </div>
                </div>
            </div>
        </div>
     </div>
</template>

<script>
export default {
    props:{
        seriesList: Array,
    },
    data(){
        return{
            firstImgPart: "https://image.tmdb.org/t/p/w500",
            stars: [],
        }
    },
     methods: {
        checkTitle(originaltitle,title){
            if(originaltitle != title){
                return true;
            }
           
        },
        showTitle(){
             if(this.seriesList.length != 0){
                return true;
            }else{
                return false;
            }
        },
            getStars(){
                this.seriesList.forEach((item)=>{
                    const array = [];
                for(let i=0; i < (Math.ceil(item.vote_average / 2)); i++){
                    array.push('star');
                }
                this.stars.push(array);
                })
            }
    },
    mounted(){
        this.getStars();
    }
}
</script>

<style lang="scss" scoped>
    @import '../style/serie.scss'
</style>