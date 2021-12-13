<template>
  <div>
    <the-header />
    <banner />
    <main class="app">
      <nuxt keep-alive />
    </main>
    <the-footer />
  </div>
</template>

<script>
export default {
  name: 'Default',
}
</script>
