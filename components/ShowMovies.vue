<template>
  <div class="movies">
    <div v-for="movie in movies.results" :key="movie.id">
      <div class="movie">
        <div class="movie_wrapper">
          <img
            class="movie_poster"
            :src="`https://image.tmdb.org/t/p/w500/${movie.poster_path}`"
            alt="poster"
          />
          <span class="rating">{{ movie.vote_average }}</span>
          <div class="overview">{{ movie.overview }}</div>
        </div>
        <div class="movie_info">
          <h4 class="movie_title">
            {{ movie.title.slice(0, 25) }}
            <span v-if="movie.title.length > 25">...</span>
          </h4>
          <p class="movie_released">
            Released:
            {{
              new Date(movie.release_date).toLocaleString('en-GB', {
                day: 'numeric',
                month: 'long',
                year: 'numeric',
              })
            }}
          </p>
          <nuxt-link :to="{ name: 'movies-movie', params: { movie: movie.id } }"
            ><button class="movie_details">Show More</button></nuxt-link
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      movies: [],
      url: `${this.$config.nowPlaying}api_key=${this.$config.apiKey}&language=en-US&page=1`,
    }
  },
  // fetch nuxt function
  async fetch() {
    this.movies = await fetch(this.url).then((res) => res.json())
  },
}
</script>

<style lang="scss" scoped>
.movies {
  padding: 80px 0;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 25px;
}

.movie {
  color: #fff;
  box-shadow: rgba(0, 0, 0, 0.3) 0px 19px 38px,
    rgba(0, 0, 0, 0.22) 0px 15px 12px;

  &_info {
    margin-left: 15px;
  }

  &_wrapper {
    position: relative;
    overflow: hidden;
    height: 420px;

    .rating {
      position: absolute;
      top: 0;
      left: 0;
      background-color: crimson;
      width: 36px;
      height: 40px;
      border-bottom-right-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .overview {
      position: absolute;
      bottom: 0;
      background-color: crimson;
      color: #fff;
      padding: 15px;
      font-size: 12px;
      transform: translateY(100%);
      transition: 0.3s ease-in-out all;
    }
  }

  &_wrapper:hover {
    .overview {
      transform: translateY(0);
    }
  }

  &_poster {
    width: 100%;
    object-fit: cover;
  }

  &_title {
    margin-top: 10px;
    font-weight: 300;
  }

  &_released {
    font-size: 12px;
    font-weight: 500;
    color: cornflowerblue;
  }

  &_details {
    background-color: crimson;
    border: none;
    outline: none;
    padding: 8px 16px;
    color: #fff;
    border-radius: 3px;
    margin-top: 8px;
    margin-bottom: 14px;
    cursor: pointer;
  }
}
</style>
