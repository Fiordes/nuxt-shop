<template>
  <nav class="mobile-submenu">
    <h2 v-if="subtitle" class="mobile-submenu__subtitle">{{ subtitle }}</h2>
    <ul class="mobile-submenu__list" v-if="submenu">
      <li
        class="mobile-submenu__item"
        v-for="item in itemList"
        :key="item.id"
        :class="typeOfListItem"
        @click.prevent="someclick"
      >
        <img
          :src="require(`~/assets/images/mobile/menu-icons/${item.icon}.svg`)"
          alt=""
          class="mobile-submenu__icon"
        />
        <a href="#" class="mobile-submenu__link">{{ item.name }}</a>
        <img
          :src="require(`~/assets/images/mobile/menu-icons/arrow-right.svg`)"
          alt=""
          class="mobile-submenu__arrow"
        />
        <Submenu :itemList="item.submenuList" />
      </li>
      <li class="mobile-submenu__item" @click="$nuxt.$emit('open-brand-modal')">
        <img
          :src="require(`~/assets/images/mobile/menu-icons/brands.svg`)"
          alt=""
          class="mobile-submenu__icon"
        />
        <a class="mobile-submenu__link" href="#">Brands</a>
        <img
          :src="require(`~/assets/images/mobile/menu-icons/arrow-right.svg`)"
          alt=""
          class="mobile-submenu__arrow"
        />
      </li>
    </ul>
    <ul v-else class="mobile-submenu__list">
      <li
        class="mobile-submenu__item"
        v-for="item in itemList"
        :key="item.id"
        :class="typeOfListItem"
      >
        <nuxt-link :to="item.link" class="mobile-submenu__link">{{
          item.name
        }}</nuxt-link>
        <img
          class="mboile-submenu__more"
          :src="require('assets/images/mobile/menu-icons/more-horizontal.svg')"
          alt=""
        />
      </li>
    </ul>
  </nav>
</template>

<script>
import gsap from "gsap";
import { TimelineMax, Power0 } from "gsap";

export default {
  props: {
    subtitle: {
      type: String,
      default: ""
    },
    submenu: {
      type: Boolean,
      default: ""
    },
    typeOfListItem: {
      type: String,
      default: ""
    },
    itemList: {
      type: Array,
      default: []
    }
  },
  methods: {
    someclick(e) {
      if (e.target.closest(".has-submenu")) {
        document.querySelectorAll(".submenu").forEach(elem => {
          elem.classList.remove("active");
        });
        let el = e.target.closest(".has-submenu");
        el.querySelector(".submenu").classList.add("active");
        this.triggerSubmenu(document.querySelector(".submenu.active"));
        this.triggerElement(document.querySelector(".mobile-submenu"));
      } else {
        el.classList.remove("active");
      }
    },

    triggerElement(el) {
      gsap.to(el, {
        x: "-120%"
      });
    },
    triggerSubmenu(el) {
      gsap.to(el, {
        opacity: 1
      });
    }
  },
  components: {
    Submenu: () => import("./Submenu")
  },
  created() {
    this.$nuxt.$on("close-sub", () => {
      gsap.to(document.querySelector(".mobile-submenu"), {
        x: 0
      });
      gsap.to(".submenu.active", {
        opacity: 0
      });
    });
  }
};
</script>

<style lang="scss">
.mobile-submenu {
  margin-bottom: 30px;
  /* overflow: hidden; */
  &_subtitle {
    font-size: 1.2em;
    letter-spacing: 0.0275em;
    margin-bottom: 16px;
  }

  &__list {
    position: relative;
  }

  &__item {
    width: 100%;

    border-bottom: 1px solid #f0f0f0;
    padding: 17px 0;
    display: flex;
    align-items: center;
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
