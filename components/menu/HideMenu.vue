<template>
  <div class="container hide-menu">
    <MobileMenu
      :itemList="productsList"
      subtitle="Products"
      :submenu="true"
      typeOfListItem=" has-submenu"
    />
    <MobileMenu :itemList="infoList" subtitle="More Info" :submenu="false" />
    <AccountMenu :itemList="accountList" />
    <transition name="modal-search">
      <SearchModal v-if="searchModalVisible" />
    </transition>
  </div>
</template>

<script>
import gsap from "gsap";
// import { TimelineMax, Power0 } from "gsap";
export default {
  data() {
    return {
      productsList: [
        {
          name: "Portable Acoustics",
          icon: "acoustic",
          submenuList: [
            { name: "1", link: "/" },
            { name: "1", link: "/" }
          ]
        },
        {
          name: "Headphones",
          icon: "headphones",
          submenuList: [
            { name: "2", link: "/" },
            { name: "2", link: "/" }
          ]
        },
        {
          name: "Laptops",
          icon: "laptop",
          submenuList: [
            { name: "3", link: "/" },
            { name: "3", link: "/" }
          ]
        },
        {
          name: "Mobile cellphones",
          icon: "phone",
          submenuList: [
            { name: "3", link: "/" },
            { name: "3", link: "/" }
          ]
        }
      ],
      infoList: [
        { name: "Some important", icon: "", link: "/" },
        { name: "More important", icon: "", link: "/" },
        { name: "Much more important", icon: "", link: "/" },
        { name: "Not important", icon: "", link: "/" }
      ],
      accountList: [
        { name: "My Order", icon: "", link: "/" },
        { name: "Loyalty program", icon: "", link: "/" },
        { name: "My profile", icon: "", link: "/" }
      ],
      searchModalVisible: false
    };
  },
  components: {
    MobileMenu: () => import("./MobileSubmenuList"),
    AccountMenu: () => import("./AccountMenu"),
    SearchModal: () => import("../modals/SearchModal")
  },
  methods: {
    triggerSearchModal() {
      this.searchModalVisible = !this.searchModalVisible;
    }
  },
  mounted() {},
  computed: {},
  created() {
    this.$nuxt.$on("open-brand-modal", () => {
      console.log("Yo from hide");
      this.triggerSearchModal();
    });
    this.$nuxt.$on("close-brand-modal", () => {
      console.log("Yo from hide");
      this.triggerSearchModal();
    });
  }
};
</script>
<style lang="scss" scoped>
.modal-search-enter-active {
  transition: all 0.3s ease;
}
.modal-search-leave-active {
  transition: all 0.4s ease-out;
}
.modal-search-enter,
.modal-search-leave-to {
  transform: translateY(100px);
  opacity: 0;
}
.hide-menu {
  position: fixed;
  top: 70px;
  left: 0;
  bottom: 0;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>
