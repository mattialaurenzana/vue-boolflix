<template>
    <div>
        <i class="fas fa-star" v-for="(film,i) in getStars[i]" :key="i"></i>
    </div>
</template>

<script>
export default {
    props:{
        vector: Array,
    },
    data(){
        return{
            stars: [],
        }
    },
    computed: {
                  getStars(){

                this.vector.forEach((item)=>{
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

</style>