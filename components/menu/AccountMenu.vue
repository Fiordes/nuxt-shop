<template>
  <div class="account-menu">
    <div class="account-menu__user">
      <a href="#" class="user-avatar">
        <img src="~/assets/images/mobile/menu-icons/user.jpg" alt="Avatar" />
      </a>
      <a href="#" class="user-name">
        <span>Stepan Bandera</span>
      </a>
      <a href="#" class="user-logout">
        <img src="~/assets/images/mobile/menu-icons/logout.svg" alt="logout" />
      </a>
    </div>
    <ul class="account-menu__list">
      <li
        class="account-menu__item"
        v-for="item in itemList"
        :key="item.id"
        :class="typeOfListItem"
      >
        <nuxt-link :to="item.link" class="account-menu__link">{{
          item.name
        }}</nuxt-link>
      </li>
      <li class="account-menu__item regime-switcher">
        <span>Change regime</span>
        <span class="regime-switcher__state"
          ><img src="~/assets/images/mobile/menu-icons/sun.svg" alt="sun" />

          Day</span
        >
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
    },
    typeOfListItem: {
      type: String,
      default: "dots-include"
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
.account-menu {
  &__user {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin-bottom: 15px;
    .user {
      &-avatar {
        width: 36px;
        height: 36px;
        img {
          width: 100%;
          height: 100%;
          border-radius: 50%;
        }
      }
      &-name {
        margin-left: 11px;
        display: block;
        font-weight: bold;
        font-size: 13px;
        letter-spacing: 0.1px;
      }
      &-logout {
        margin-left: auto;
      }
    }
  }
  &__item {
    position: relative;
    width: 100%;
    position: relative;
    border-bottom: 1px solid #f0f0f0;
    padding: 17px 0;
    display: flex;
    align-items: center;
    &:last-child {
      border-bottom: none;
    }

    &.dots-include {
      &:after {
        content: "";
        display: block;
        width: 15px;
        height: 15px;
        background: url("../../assets/images/mobile/menu-icons/more-horizontal.svg");
        background-size: cover;
        background-repeat: no-repeat;
        position: absolute;
        top: calc(50% - 8px);
        right: 0;
      }
    }

    &.regime-switcher {
      display: flex;
      justify-content: space-between;
      align-items: center;
      span {
        &:nth-child(2) {
          display: flex;
          align-items: center;
          cursor: pointer;
          img {
            margin-right: 12px;
          }
        }
      }
    }
  }
}
</style>
