<template>
    <div class="main">
            <home-page :mostPopular="mostPopular" :topRated="topRated" v-if="homePage"/>
            <film-list :listFilm="filmList"/>
            <series-list :seriesList="seriesList"/>
    </div>
</template>

<script> 
import filmList from './filmList.vue'
import seriesList from './seriesList.vue'
import homePage from './homePage.vue'
export default {

    components: {
        homePage,
        filmList,
        seriesList,
    },
    props: {
        filmList: Array,
        seriesList: Array,
        mostPopular: Array,
        homePage: Boolean,
        topRated: Array,
    },
   
}
</script>

<style lang="scss" scoped>

    @import '../style/mainContainer.scss'
    
</style>