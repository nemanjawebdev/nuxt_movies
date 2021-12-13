<template>
  <div class="banner">
    <div class="img-wrapper">
      <nuxt-img src="banner-films.jpg" alt="banner" />
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.banner {
  height: 250px;
  object-fit: cover;
  overflow: hidden;
  background-color: #001325;
}

.img-wrapper {
  position: relative;
}
</style>
