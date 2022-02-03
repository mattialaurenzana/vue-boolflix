<template>
    <div class="main">
        <div class="row">
            <div v-for="(film,index) in titlelists" :key="index" class="card">
                <div class="img-container">
                    <img :src="firstImgPart+film.poster_path" alt="">
                </div>
            </div>
        </div>
    </div>
</template>

<script> 
export default {
    data(){
        return{
            firstImgPart: "https://image.tmdb.org/t/p/w342",
        }
    },
    props: {
        titlelists: Array,
    }
}
</script>

<style lang="scss" scoped>

    .main{
       
        width: 90%;
        margin: 20px auto;

       .row{
           gap: 15px;
           justify-content: center;
            .card{
            background-color: black;
            width: calc((100% / 5) - 15px);
            color: white;
            padding: 10px;
            display: flex;
            flex-direction: column;
            align-items: center;
            word-break: break-word;

            .img-container{
                img{
                    width: 100%;
                    height: 100%;
                }
            }
        }
       }
    }
</style>