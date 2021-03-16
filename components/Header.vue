<template>
  <div>
    <header class="mobile-header">
      <div class="mobile-header__row">
        <!-- Burger -->
        <div
          class="mobile-header__burger"
          :class="[burgerState ? 'active' : '']"
          @click="changeBurgerState"
        >
          <span></span>
          <span></span>
          <span></span>
        </div>
        <!-- Logo -->
        <div class="mobile-header__logo">
          <img src="~/assets/images/mobile/logo-moible.svg" alt="" />
        </div>
        <!-- Cart/Search -->
        <div
          class="mobile-header__switcher"
          :class="[burgerState ? 'show-search' : 'show-cart']"
        >
          <div class="switcher__cart cart">
            <img src="~/assets/images/mobile/shopping-cart.svg" alt="" />
          </div>
          <div class="switcher__search search">
            <img src="~/assets/images/mobile/search.svg" alt="" />
          </div>
        </div>
        <transition name="menu">
          <HideMenu v-if="burgerState" />
        </transition>
      </div>
    </header>
  </div>
</template>

<script>
import gsap from "gsap";
import { TimelineMax, Power0 } from "gsap";

export default {
  data() {
    return {
      burgerState: false,
      tween: new TimelineMax({
        defaults: {
          duration: 0.9
        }
      })
    };
  },
  components: {
    HideMenu: () => import("./menu/HideMenu")
  },
  methods: {
    changeBurgerState() {
      this.burgerState = !this.burgerState;
    },
    menuAnimation() {
      this.tween.fromTo(
        ".hide-menu",
        {
          y: "100%",
          opacity: 0
        },
        {
          y: 0,
          opacity: 1
        }
      );
    },
    reverseAnimation() {
      this.tween.timeScale(2);
      this.tween.reverse();
    }
  },
  mounted() {},
  computed: {},
  watch: {}
};
</script>
<style lang="scss">
.menu-enter-active {
  transition: all 0.3s ease;
}
.menu-leave-active {
  transition: all 0.5s cubic-bezier(1, 0.5, 0.8, 1);
}
.menu-enter,
.menu-leave-to {
  transform: translateY(100px);
  opacity: 0;
}

.mobile-header {
  @include media(desktop) {
    display: none;
  }
  &__nav {
    display: none;
  }
  &__row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 16px 35px;
  }

  &__burger {
    width: 23px;
    height: 23px;
    position: relative;
    cursor: pointer;
    display: flex;
    align-items: flex-start;
    justify-content: space-around;
    flex-direction: column;
    span {
      display: block;
      width: 100%;
      height: 2px;
      border-radius: 8px;
      background-color: $font-color;
      transition: all 0.3s;

      &:nth-child(1) {
        transform: translateY(0) rotate(0);
      }
      &:nth-child(2) {
        transform: translateY(0) rotate(0);
      }

      &:nth-child(3) {
        width: 50%;
      }
    }
    &.active {
      span {
        transform-origin: center;
        &:nth-child(1) {
          transform: translateY(7px) rotate(45deg);
        }
        &:nth-child(2) {
          transform: translateY(-1px) rotate(-45deg);
        }
        &:nth-child(3) {
          width: 0;
        }
      }
    }
  }

  &__switcher {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 25px;
    height: 27px;

    overflow: hidden;

    div {
      position: absolute;
      left: 0;
      transition: all 0.3s;
      cursor: pointer;
    }

    &.show-cart {
      .cart {
        bottom: 0;
      }
      .search {
        top: -120%;
      }
    }
    &.show-search {
      .cart {
        bottom: 110%;
      }
      .search {
        top: 0;
      }
    }
  }
}
</style>
