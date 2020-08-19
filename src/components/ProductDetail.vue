<template>
  <div class="ProductDetail">
    <section class="padding-top-50 padding-bottom-50">
      <div class="container">
        <!-- SHOP DETAIL -->
        <div class="shop-detail">
          <div class="row">
            <!-- Popular Images Slider -->
            <div class="col-md-7">
              <!-- Images Slider -->
              <div class="product-pic-zoom" v-if="productDetails.galleries.length>0">
                <img class="product-big-img" :src="thumbsholder" alt />
              </div>
              <div class="no-image" v-else>
                <img class src="images/logo-no.jpg" />
              </div>
              <div class="images-slider margin-top-20">
                <ul class="slides" v-if="productDetails.galleries.length>0">
                  <carousel :nav="false" :dots="false" class="product-thumbs-track ps-slider">
                    <div
                      v-for="images in productDetails.galleries"
                      :key="images.id"
                      class="pt"
                      @click="changeImage(images.picture)"
                    >
                      <img
                        class="padding-left-10"
                        :class="images.picture == thumbsholder ? 'active-carousel': ''"
                        :src="images.picture"
                        alt
                      />
                    </div>
                  </carousel>
                </ul>
              </div>
            </div>

            <!-- COntent -->
            <div class="col-md-5 name-product">
              <h4>{{productDetails.name}}</h4>
              <span class="price">
                <small>Rp</small>
                {{productDetails.po_details[0].price_r}}
              </span>

              <!-- Short By -->
              <div class="some-info">
                <ul class="row">
                  <!-- COLORS -->
                  <li class="col-xs-8">
                    <ul
                      class="colors-shop"
                      v-if="productDetails.product_details && productDetails.product_details>0"
                    >
                      <li>
                        <span class="margin-right-20">
                          <b>Colors</b>
                        </span>
                      </li>
                      <ul v-for="(variant) in productDetails.product_details" :key="variant.id">
                        <li class="padding-right-5">{{variant.variant}}</li>
                      </ul>
                    </ul>
                    <ul v-else>
                      <li></li>
                    </ul>
                  </li>

                  <!-- ADD TO CART -->
                  <li class="col-xs-6">
                    <a
                      @click.prevent="hrefWa(productDetails.name)"
                      href="#"
                      class="btn"
                    >Pesan Sekarang</a>
                  </li>
                </ul>

                <!-- INFOMATION -->
                <div class="inner-info">
                  <h6>How To Order</h6>
                  <p
                    class="margin-bottom-20"
                  >Pesan sekarang untuk langsung berhubungan dengan admin kami</p>
                  <h6>SHIPPING & RETURNS</h6>
                  <p class="margin-bottom-20">Cash On Delivery or Transfer</p>
                  <h6>Marketplace</h6>
                  <div class="row text-center margin-top-20">
                    <a href="http://" target="_blank" rel="noopener noreferrer">
                      <img
                        src="https://www.freepnglogos.com/uploads/logo-tokopedia-png/berita-tokopedia-info-berita-terbaru-tokopedia-6.png"
                        width="50"
                      />
                    </a>
                    <a href="http://" target="_blank" rel="noopener noreferrer">
                      <img
                        src="https://www.pngmart.com/files/12/Shopee-Logo-Transparent-Background.png"
                        width="50"
                      />
                    </a>
                    <a href="http://" target="_blank" rel="noopener noreferrer">
                      <img
                        src="https://www.vhv.rs/dpng/d/590-5906735_icon-logo-lazada-png-icon-lazada-logo-png.png"
                        width="50"
                      />
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!--======= PRODUCT DESCRIPTION =========-->
        <div class="item-decribe">
          <!-- Nav tabs -->
          <ul class="nav nav-tabs animate fadeInUp" data-wow-delay="0.4s" role="tablist">
            <li role="presentation" class="active">
              <a href="#descr" role="tab" data-toggle="tab">DESCRIPTION</a>
            </li>
          </ul>

          <!-- Tab panes -->
          <div class="tab-content animate fadeInUp" data-wow-delay="0.4s">
            <!-- DESCRIPTION -->
            <div role="tabpanel" class="tab-pane fade in active" id="descr">
              <p v-html="productDetails.description"></p>
            </div>
          </div>
        </div>
      </div>
    </section>
    <RelatedProduct :type="productDetails.type" />
  </div>
</template>

<script>
import carousel from "vue-owl-carousel";
import RelatedProduct from "@/components/RelatedProduct.vue";

import axios from "axios";

export default {
  name: "ProductDetail",
  components: {
    carousel,
    RelatedProduct,
  },
  data() {
    return {
      thumbsholder: "",
      productDetails: [],
    };
  },
  methods: {
    hrefWa(nameProduct) {
      var link =
        "https://api.whatsapp.com/send?phone=6282249005206&text=Hi%20Admin%2C%20mau%20order%20produk%20" +
        nameProduct +
        "%20dong!!!";
      window.open(link, "_blank");
    },
    changeImage(urlImage) {
      this.thumbsholder = urlImage;
    },
    setDataPicture(data) {
      this.productDetails = data;
      this.thumbsholder = data.galleries[0].picture;
    },
  },
  mounted() {
    axios
      .get("https://dashboard.sejatistore.my.id/api/product", {
        params: {
          slug: this.$route.params.slug,
        },
      })
      .then((res) => this.setDataPicture(res.data.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.images-slider .pt {
  margin-right: 10px;
}
.images-slider .pt img {
  width: 15vw;
  height: 15vw;
}
.product-pic-zoom img {
  width: 48vw;
  height: 48vw;
}
@media (max-width: 575.98px) {
  .images-slider .pt img {
    width: 28vw;
    height: 28vw;
  }
  .product-pic-zoom img {
    width: 90vw;
    height: 90vw;
  }
  .name-product {
    margin-top: 40px;
  }
}

@media (min-width: 576px) and (max-width: 991.98px) {
  .images-slider .pt img {
    width: 30vw;
    height: 30vw;
  }
  .product-pic-zoom img {
    width: 80vw;
    height: 80vw;
  }
  .name-product {
    margin-top: 40px;
  }
}
.no-image img {
  width: 100%;
}
.active-carousel {
  border: 2px solid peru;
}
</style>