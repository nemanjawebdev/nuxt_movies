<template>
  <header class="header">
    <nav class="main_nav container">
      <nuxt-link :to="{ name: 'index' }">
        <div class="main_nav_logo">TMDB</div>
      </nuxt-link>

      <div class="main_nav_links">
        <NuxtLink class="main_nav_link" :to="{ name: 'index' }">Home</NuxtLink>
        <NuxtLink class="main_nav_link" :to="{ name: 'movies' }"
          >Movies</NuxtLink
        >
        <NuxtLink class="main_nav_link" :to="{ name: 'series' }"
          >TV Show</NuxtLink
        >
      </div>
    </nav>
  </header>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.header {
  position: sticky;
  top: 0;
  height: 70px;
  width: 100%;
  backdrop-filter: saturate(180%) blur(10px);
  z-index: 99;
}

// @supports (-webkit-backdrop-filter: saturate(180%) blur(10px)) or
//   (backdrop-filter: saturate(180%) blur(10px)) {
//   .header {
//     -webkit-backdrop-filter: saturate(180%) blur(10px);
//     backdrop-filter: saturate(180%) blur(10px);
//   }
// }

.main_nav {
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;

  &_logo {
    font-size: 22px;
    font-weight: 600;
    font-weight: 500;
    letter-spacing: 1.5px;
    width: auto;
    color: #fff;
  }

  &_link {
    margin-right: 25px;
    color: rgb(176, 174, 179);
  }

  &_link:last-child {
    margin-right: 0;
  }
}

.nuxt-link-exact-active {
  color: #fff;
}
</style>
