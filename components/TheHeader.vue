<template>
  <header class="header">
    <nav class="nav container">
      <div class="logo">Logo</div>
      <div class="links">
        <NuxtLink class="nav-link" to="/">Home</NuxtLink>
        <NuxtLink class="nav-link" to="/about">About</NuxtLink>
        <NuxtLink class="nav-link" to="/">Home</NuxtLink>
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
  height: 10vh;
  width: 100%;
  background: hsl(0 0% 100% / 0.1);
  backdrop-filter: saturate(180%) blur(10px);
}

// @supports (-webkit-backdrop-filter: saturate(180%) blur(10px)) or
//   (backdrop-filter: saturate(180%) blur(10px)) {
//   .header {
//     -webkit-backdrop-filter: saturate(180%) blur(10px);
//     backdrop-filter: saturate(180%) blur(10px);
//   }
// }

.nav {
  height: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  height: 20px;
  width: auto;
  color: #fff;
}

.nav-link {
  margin-right: 25px;
  color: #fff;
}

.nav-link:last-child {
  margin-right: 0;
}
</style>
