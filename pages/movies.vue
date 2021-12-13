<template>
  <div>
    <div class="container">
      <input
        v-model="searchInput"
        type="text"
        placeholder="search movie ..."
        @keyup.enter="$fetch"
      />
      <show-movies :movies="movies" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      movies: [],
      // url: `https://api.themoviedb.org/3/movie/upcoming?api_key=${this.$config.apiKey}&language=en-US&page=1`,
      trending: `https://api.themoviedb.org/3/movie/popular?api_key=2034353c3c4368999a00554aecd8ab8d&language=en-US&page=1`,
    }
  },
  async fetch() {
    this.movies = await fetch(this.trending).then((res) => res.json())
  },
  head: {
    title: 'Trending Movies',
  },
}
</script>

<style lang="scss" scoped>
input {
  margin-top: 50px;
  border: none;
  outline: none;
  padding: 12px;
  width: 400px;
}
</style>
