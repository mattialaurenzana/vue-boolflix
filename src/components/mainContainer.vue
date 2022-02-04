<template>
    <div class="main">
            <film-list :listFilm="filmList"/>
            <series-list :seriesList="seriesList"/>
    </div>
</template>

<script> 
import filmList from './filmList.vue'
import seriesList from './seriesList.vue'
export default {

    components: {
        filmList,
        seriesList,
    },
    props: {
        filmList: Array,
        seriesList: Array,
    },
   
}
</script>

<style lang="scss" scoped>

    @import '../style/mainContainer.scss'
    
</style>