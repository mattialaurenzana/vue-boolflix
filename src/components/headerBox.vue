<template>
    <header>
        <div class="title-container">
            <h1>BOOLFLIX</h1>
        </div>
        <div class="input-container">
            <input type="text" v-model="inputResearch">
            <button @click="$emit('search',inputResearch)">Search</button>
        </div>
    </header>
</template>

<script>
export default {
    data(){
        return{
            inputResearch : "",
        }
    }
}
</script>

<style lang="scss" scoped>

    header{
        background-color: black;
        height: 100px;
        padding: 10px;
        display: flex;
        align-items: center;
        justify-content: space-between;

        .title-container{
            h1{
                color: red;
            }
        }

        .input-container{
            display: flex;
            gap: 10px;
        }

        
    }
</style>