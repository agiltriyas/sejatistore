<template>
  <div class="relatedproduct">
    <section class="light-gray-bg padding-top-50 padding-bottom-150">
      <div class="container">
        <!-- Main Heading -->
        <div class="heading text-center">
          <h4>RELATED PRODUCT</h4>
        </div>
        <div v-if="productRelated.length>0" class="papular-block block-slide">
          <!-- Popular Item Slide -->
          <carousel
            :responsive="{0:{items:3},800:{items:4}}"
            :nav="true"
            :autoplay="true"
            :dots="false"
          >
            <!-- Item -->
            <div v-for="prodRel in productRelated" :key="prodRel.id" class="item">
              <!-- Item img -->
              <div class="item-img">
                <img class="img-1" :src="prodRel.galleries[0].picture" alt />
                <img class="img-2" :src="prodRel.galleries[1].picture" alt />
                <!-- Overlay -->
                <div class="overlay">
                  <div class="position-center-center">
                    <div class="inn">
                      <a :href="prodRel.galleries[0].picture" data-lighter>
                        <i class="icon-magnifier"></i>
                      </a>
                    </div>
                  </div>
                </div>
              </div>
              <!-- Item Name -->
              <div class="item-name">
                <router-link :to="'/product/'+prodRel.slug">{{prodRel.name.slice(0,15)}}</router-link>
              </div>
              <!-- Price -->
              <span class="price">
                <small>Rp</small>
                {{prodRel.po_details[0].price_r}}
              </span>
            </div>
          </carousel>
        </div>
        <div class v-else></div>
      </div>
    </section>
  </div>
</template>

<script>
import carousel from "vue-owl-carousel";
import axios from "axios";

export default {
  name: "RelatedProduct",
  components: {
    carousel,
  },
  props: ["type"],
  data() {
    return {
      productRelated: [],
    };
  },
  mounted() {
    axios
      .get("http://dashboard.sejatistore.my.id/api/product", {
        params: {
          type: this.$props.type,
        },
      })
      .then((res) => (this.productRelated = res.data.data.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.papular-block .item-img {
  width: 20vw;
  height: 20vw;
}
.papular-block .overlay {
  width: 20vw;
}

@media (max-width: 575.98px) {
  .papular-block .item-img {
    width: 30vw;
    height: 30vw;
  }
  .papular-block .overlay {
    width: 30vw;
  }
}

@media (min-width: 576px) and (max-width: 991.98px) {
  .papular-block .item-img {
    width: 25vw;
    height: 25vw;
  }
  .papular-block .overlay {
    width: 25vw;
  }
}
</style>