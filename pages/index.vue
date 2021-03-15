<template>
  <div class="container">
    Hello
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  components: {},
  methods: {},
  mounted() {},
  computed: {}
};
</script>
<style lang="scss" scoped>
.container {
  @include media(wide) {
    display: none;
  }
}
</style>
