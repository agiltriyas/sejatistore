<template>
  <div class="product">
    <Header />
    <ProductDetail />
    <Footer />
  </div>
</template>
<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import ProductDetail from "@/components/ProductDetail.vue";

export default {
  name: "Product",
  components: {
    Header,
    Footer,
    ProductDetail
  }
};
</script>

<style scoped>
</style>