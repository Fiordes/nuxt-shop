<template>
  <nav class="mobile-nav">
    <h2 class="mobile-nav__subtitle">{{ subtitle }}</h2>
    <ul class="mobile-nav__list" :class="typeOfList"></ul>
  </nav>
</template>

<script>
export default {
  props: {
    subtitle: {
      type: String,
      default: ""
    },

    typeOfList: {
      type: String,
      default: ""
    }
  },
  methods: {
    hard(e) {
      console.log("yo");
    },
    simple(e) {
      console.log("yo");
    }
  }
};
</script>

<style lang="scss">
.mobile-nav {
  &_subtitle {
    font-size: 1.2em;
    letter-spacing: 0.0275em;
    margin-bottom: 16px;
  }

  &__item {
    width: 100%;
    position: relative;
    border-bottom: 1px solid #f0f0f0;
    padding: 17px 0;
    &:last-child {
      border-bottom: none;
    }

    &.arrow-include {
      &:after {
        content: "";
        display: block;
        width: 15px;
        height: 15px;
        background: url("../../assets/images/mobile/menu-icons/arrow-right.svg");
        background-size: cover;
        background-repeat: no-repeat;
        position: absolute;
        top: calc(50% - 8px);
        right: 0;
      }
    }
  }

  &__link {
    font-size: 14px;
    letter-spacing: 0.0275em;
    position: relative;
    width: 100%;
  }
  &__icon {
    margin-right: 12px;
  }
}
</style>
