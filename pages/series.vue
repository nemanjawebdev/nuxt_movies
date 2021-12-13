<template>
  <div class="container">
    <input
      v-model="searchInput"
      type="text"
      placeholder="search movie ..."
      @keyup.enter="$fetch"
    />
    <show-series :tvshow="tvshow" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      tvshow: [],
      url: `https://api.themoviedb.org/3/tv/popular?api_key=${this.$config.apiKey}&language=en-US&page=1`,
    }
  },
  async fetch() {
    this.tvshow = await fetch(this.url).then((res) => res.json())
  },
  head: {
    title: 'TV Show',
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
