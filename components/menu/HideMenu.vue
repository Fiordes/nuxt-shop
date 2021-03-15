<template>
  <div class="container">
    <MobileMenu
      :itemSubClass="true"
      :isLink="true"
      typeOfList="submenu"
      :itemList="productsList"
      subtitle="Products"
    />
    <MobileMenu subtitle="Info" :isLink="false" :itemList="infoList" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      productsList: [
        { name: "Portable Acoustics", icon: "acoustic" },
        { name: "Headphones", icon: "headphones" },
        { name: "Laptops", icon: "laptop" },
        { name: "Mobile cellphones", icon: "phone" },
        { name: "Brands", icon: "brands" }
      ],
      infoList: [
        { name: "Some important", icon: "" },
        { name: "More important", icon: "" },
        { name: "Much more important", icon: "" },
        { name: "Not important", icon: "" }
      ]
    };
  },
  components: {
    MobileMenu: () => import("./MobileMenu")
  },
  methods: {},
  mounted() {},
  computed: {}
};
</script>
<style lang="scss" scoped></style>
