<template>
  <div class="banner">
    <the-header />
    <div class="img-wrapper">
      <img src="../assets/images/banner-films.jpg" alt="banner" />
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.banner {
  position: relative;
  min-height: 40vh;
  background-color: #001325;
}

.banner::after {
  content: '';
  position: absolute;
  inset: 0;
  background-color: #001325;
}

.img-wrapper > img {
  width: 100%;
}
</style>
