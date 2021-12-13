<template>
  <div class="container">
    <h1>{{ tvshow.name }}</h1>
  </div>
</template>

<script>
export default {
  async asyncData({ $config, params, $axios }) {
    const tvshow = await $axios.$get(
      `https://api.themoviedb.org/3/tv/${params.tvshow}?api_key=${$config.apiKey}&language=en-US`
    )
    return { tvshow }
  },
  head: {
    title: 'Tv Show details',
  },
}
</script>

<style lang="scss" scoped></style>
