<template>
  <div>
    <div class="container">
      <div class="search">
        <input
          v-model="searchInput"
          type="text"
          placeholder="search movie ..."
          @keyup.enter="$fetch"
        />
      </div>

      <show-movies v-if="searchInput === ''" :movies="movies" />
      <searched-movie v-else :movies="movies" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      movies: [],
      searchInput: '',
      now_playing: `${this.$config.nowPlaying}api_key=${this.$config.apiKey}&language=en-US&page=1`,
    }
  },
  fetchDelay: 1000,
  async fetch() {
    if (this.searchInput === '') {
      await this.getMovies()
    } else {
      await this.searchedMovie(this.searchInput)
    }
  },
  methods: {
    async getMovies() {
      this.movies = await fetch(this.now_playing).then((res) => res.json())
      // .catch((error) => console.log(error))
    },
    async searchedMovie(query) {
      this.searchInput = ''
      this.movies = await fetch(
        `https://api.themoviedb.org/3/search/movie?api_key=${this.$config.apiKey}&language=en-US&query=${query}&page=1&include_adult=false`
      ).then((res) => res.json())
      // .catch((error) => console.log(error))
    },
  },
}
</script>

<style lang="scss" scoped>
input {
  border: none;
  outline: none;
  padding: 12px;
  width: 400px;
}

.search {
  margin-top: 50px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
