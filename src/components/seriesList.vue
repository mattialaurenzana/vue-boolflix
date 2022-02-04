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
                        <img src="../../public/flags/US.png" alt="US flag">
                       
                    </div>
                    <div>
                        <span>Voto:</span>{{serie.vote_average}}
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
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '../style/serie.scss'
</style>