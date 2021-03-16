<template>
  <div class="submenu">
    <ul>
      <li class="submenu-back" @click.stop="$nuxt.$emit('close-sub')">
        <img
          src="~/assets/images/mobile/menu-icons/arrow-left.svg"
          alt="back"
        />
        <span>back</span>
      </li>
      <li v-for="item in itemList" :key="item.id">
        <nuxt-link :to="item.link">{{ item.name }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    itemList: {
      type: Array,
      default: []
    }
  },
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
.submenu {
  position: absolute;
  top: -30px;
  width: 100%;
  transform: translateX(120%);
  height: 311px;
  background: #fff;
  z-index: 10;
  opacity: 0;

  &.active {
  }

  &-back {
    img {
      margin-right: 16px;
    }
    span {
      color: $accent-color;
      letter-spacing: 0.0275em;
      font-weight: bold;
    }
  }
  ul {
    width: 100%;

    li {
      width: 100%;
      border-bottom: 1px solid #f0f0f0;
      padding: 17px 0;
      display: flex;
      align-items: center;
    }
  }
}
</style>
