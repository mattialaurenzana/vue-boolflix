<template>
    <div class="main">
        <div class="row">
            <div v-for="(film,index) in titlelists" :key="index" class="card">
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
                        <span>Lingua:</span>{{film.original_language}}
                    </div>
                    <div>
                        <span>Voto:</span>{{film.vote_average}}
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
            
        }
    },
    props: {
        titlelists: Array,
    },
    methods: {
        checkTitle(originaltitle,title){
            if(originaltitle != title){
                return true;
            }
           
        }
    }
}
</script>

<style lang="scss" scoped>

    .main{
       
        width: 85%;
        margin: 20px auto;

       .row{
           gap: 15px;
           justify-content: center;

            .card{
            background-color: black;
            width: calc((100% / 5) - 15px);
            color: white;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            word-break: break-word;
            position: relative;
            

            &:hover{
                cursor: pointer;
            }

            &:hover img{
                display: none;
            }

            &:hover .film-data{
                display: block;
            }

            .img-container{
                width: 100%;
                height: 100%;
                img{
                    width: 100%;
                    height: 100%;
                    
                }
            }

            .film-data{
                width: 100%;
                height: 100%;
                position: absolute;
                top: 0;
                display: none;
                font-size: 11px;
                padding: 15px;
                

                div{
                    margin: 5px 0;
                    word-break: break-word;
                    span{
                        font-weight: bold;
                        font-size: 12px;
                    }
                }
            }
        }
       }
    }
</style>