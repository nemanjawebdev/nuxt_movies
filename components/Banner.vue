<template>
  <div class="banner">
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
  height: 450px;
  object-fit: cover;
  overflow: hidden;
  background-color: #001325;
}

.banner::after {
  content: '';
}

.img-wrapper > img {
  width: 100%;
}
</style>
