<template>
  <div class="search-modal">
    <div class="container">
      <h2>Modal</h2>

      <a href="#" @click="$nuxt.$emit('close-brand-modal')">click</a>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.search-modal {
  position: fixed;
  top: 70px;
  left: 0;
  bottom: 0;
  right: 0;
  background: #fff;
  z-index: 11;
}
</style>
