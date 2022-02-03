<template>
    <div class="main">
        <div v-for="(film,index) in titlelists" :key="index" class="card">
            <img :src="film.poster_path" alt="">
            <span>{{film.title}}</span>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        titlelists: Array,
    }
}
</script>

<style lang="scss" scoped>

    .main{
        height: calc(100vh - 100px);
        background-color: grey;
        display: flex;
        flex-wrap: wrap;
        width: 80%;
        margin: 20px auto;

        .card{
            background-color: black;
            width: 100px;
            height: 200px;
            color: white;
        }
    }
</style>