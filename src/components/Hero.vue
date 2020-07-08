<template>
  <div class="hero">
    <!-- Popular Products -->
    <section class="shop-page padding-top-100 padding-bottom-50">
      <div class="container">
        <div class="item-display">
          <div class="row">
            <div class="col-xs-6">
              <span
                class="product-num text-left"
              >Showing {{from}} - {{perpage}} of {{total}} products</span>
            </div>

            <!-- Products Select -->
            <div class="col-xs-6">
              <div class="pull-right">
                <!-- GRID & LIST -->
                <a href="#." class="grid-style">
                  <i class="icon-grid"></i>
                </a>
                <a href="#." class="list-style">
                  <i class="icon-list"></i>
                </a>
              </div>
            </div>
          </div>
        </div>

        <!-- Popular Item Slide -->
        <div class="papular-block row" v-if="products.length>0">
          <!-- Item -->
          <div class="col-md-3" v-for="itemProduct in products" v-bind:key="itemProduct.id">
            <div class="item">
              <!-- Item img -->
              <div class="item-img">
                <img
                  class="img-1"
                  v-if="itemProduct.galleries[0]"
                  :src="itemProduct.galleries[0].picture"
                  alt
                  style="max-height:270px"
                />
                <img class="img-1" v-else src="images/logo-no.jpg" alt />

                <img
                  class="img-2"
                  v-if="itemProduct.galleries[1]"
                  :src="itemProduct.galleries[1].picture"
                  alt
                  style="max-height:270px"
                />

                <img class="img-2" v-else src="images/logo-no.jpg" alt />
                <!-- Overlay -->
                <div class="overlay">
                  <div class="position-center-center">
                    <div class="inn">
                      <a
                        v-if="itemProduct.galleries[0]"
                        :href="itemProduct.galleries[0].picture"
                        data-lighter
                      >
                        <i class="icon-magnifier"></i>
                      </a>
                      <a v-else href="images/logo-no.jpg" data-lighter>
                        <i class="icon-magnifier"></i>
                      </a>
                    </div>
                  </div>
                </div>
              </div>
              <!-- Item Name -->
              <div class="item-name">
                <router-link :to="'/product/'+itemProduct.slug">{{itemProduct.name.slice(0,15)}}</router-link>
              </div>
              <!-- Price -->
              <span class="price">
                <small>Rp.</small>
                {{itemProduct.po_details[0].price_r}}
              </span>
            </div>
          </div>
        </div>
        <div v-else class="papular-block row">
          <h4>Data tidak tersedia</h4>
        </div>
        <div class="papular-block row padding-bottom-50">
          <nav v-cloak>
            <ul class="flex-direction-nav">
              <li class="flex-nav-prev" v-if="prevpage">
                <a
                  class="flex-prev"
                  @click.prevent="getProducts(prevpage,perpage)"
                  :href="prevpage"
                >Previous</a>
              </li>
              <li class="flex-nav-next" v-if="nextpage">
                <a
                  class="flex-next"
                  @click.prevent="getProducts(nextpage,perpage)"
                  :href="nextpage"
                >Next</a>
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Hero",
  data() {
    return {
      thumbsholder: "",
      products: [],
      nextpage: "",
      prevpage: "",
      perpage: "",
      total: "",
      from: ""
    };
  },
  mounted() {
    axios
      .get("http://127.0.0.1:8001/api/product", {
        params: {
          limit: 9
        }
      })
      .then(res => {
        this.products = res.data.data.data;
        this.nextpage = res.data.data.next_page_url;
        this.prevpage = res.data.data.prev_page_url;
        this.perpage = res.data.data.per_page;
        this.total = res.data.data.total;
        this.from = res.data.data.from;
      })
      .catch(err => console.log(err));
  },
  methods: {
    getProducts(url, limit) {
      axios
        .get(url, {
          params: {
            limit: limit
          }
        })
        .then(res => {
          this.products = res.data.data.data;
          this.nextpage = res.data.data.next_page_url;
          this.prevpage = res.data.data.prev_page_url;
          this.from = res.data.data.from;
        })
        .catch(err => console.log(err));
    }
  }
};
</script>