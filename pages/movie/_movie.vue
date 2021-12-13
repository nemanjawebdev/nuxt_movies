<template>
  <div class="container">
    <div>{{ movie.title }}</div>
  </div>
</template>

<script>
export default {
  async asyncData({ $config, params, $axios }) {
    const movie = await $axios.$get(
      `https://api.themoviedb.org/3/movie/${params.movie}?api_key=${$config.apiKey}&language=en-US`
    )
    return { movie }
  },
  head: {
    title: 'Movie details',
  },
}
</script>

<style lang="scss" scoped>
div {
  color: #fff;
}
</style>
