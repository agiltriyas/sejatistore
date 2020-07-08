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
              <div class="images-slider">
                <ul class="slides">
                  <li data-thumb="images/large-img-1.jpg">
                    <img class="img-responsive" src="images/large-img-1.jpg" alt />
                  </li>
                  <li data-thumb="images/large-img-2.jpg">
                    <img class="img-responsive" src="images/large-img-2.jpg" alt />
                  </li>
                  <li data-thumb="images/large-img-3.jpg">
                    <img class="img-responsive" src="images/large-img-3.jpg" alt />
                  </li>
                </ul>
              </div>
            </div>

            <!-- COntent -->
            <div class="col-md-5">
              <h4>{{productDetails.name}}</h4>
              <span class="price padding-bottom-20">
                <small>Rp</small>
                {{productDetails.po_details[0].price_r}}
              </span>

              <!-- Short By -->
              <div class="some-info">
                <ul class="row margin-top-10">
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
                  <p>Pesan sekarang untuk langsung berhubungan dengan admin kami</p>
                  <h6>SHIPPING & RETURNS</h6>
                  <p>Cash On Delivery or Transfer</p>
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
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "ProductDetail",
  data() {
    return {
      productDetails: []
    };
  },
  mounted() {
    axios
      .get("http://127.0.0.1:8001/api/product", {
        params: {
          slug: this.$route.params.slug
        }
      })
      .then(res => (this.productDetails = res.data.data))
      .catch(err => console.log(err));
  },
  methods: {
    hrefWa(nameProduct) {
      var link =
        "https://api.whatsapp.com/send?phone=6282249005206&text=Hi%20Admin%2C%20mau%20order%20produk%20" +
        nameProduct +
        "%20dong!!!";
      window.open(link, "_blank");
    }
  }
};
</script>