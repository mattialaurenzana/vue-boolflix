<template>
  <div>
    <i class="fas fa-star" v-for="(film, i) in Math.ceil(film.vote_average / 2)" :key="i"></i>
  </div>
</template>

<script>
export default {
  props: {
    film: Object,
  },

};
</script>

<style lang="scss" scoped>
div{
    display: inline-block;
}
</style>