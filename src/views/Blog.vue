<template>
  <div class="blog">
    <Header />
    <Banner :tbanner="'News / Blog'" />
    <div id="content">
      <!-- Blog List -->
      <section class="blog-list blog-list-3 padding-top-100 padding-bottom-100">
        <div class="container">
          <div class="row">
            <div v-if="dataBlog.length > 0" class="col-md-9">
              <!-- Article -->
              <article v-for="blogs in dataBlog" :key="blogs.id">
                <div class="row">
                  <div class="col-sm-5">
                    <!-- Post Img -->
                    <img
                      class="img-responsive"
                      :src="blogs.imagethumb"
                      alt=""
                    />
                  </div>
                  <div class="col-sm-7">
                    <!-- Tittle -->
                    <div class="post-tittle left">
                      <router-link
                        :cat="blogs.category"
                        :to="'/blog/' + blogs.slug"
                        :blog="dataBlog"
                        class="tittle"
                        >{{ blogs.title }}</router-link
                      >
                      <!-- Post Info -->
                      <span
                        ><i class="primary-color icon-user"></i> by admin</span
                      >
                      <span
                        ><i class="primary-color icon-calendar"></i>
                        {{ blogs.created_at }}</span
                      >
                      <span
                        ><i class="primary-color icon-tag"></i>
                        {{ blogs.category }}</span
                      >
                    </div>
                    <!-- Post Content -->
                    <div class="text-left">
                      <p>{{ blogs.content.slice(0, 300) }} ...</p>
                      <router-link :to="'/blog/' + blogs.slug" class="red-more"
                        >READ MORE</router-link
                      >
                    </div>
                  </div>
                </div>
              </article>

              <!-- Pagination -->
              <ul class="pagination in-center">
                <li v-if="prevpage">
                  <a @click.prevent="getBlogs(prevpage, perpage)"
                    ><i class="fa fa-angle-left"></i
                  ></a>
                </li>
                <li
                  :class="currentpage == i ? 'active' : ''"
                  v-for="i in total"
                  :key="i"
                >
                  <a
                    @click.prevent="getBlogs(path + '?page=' + i, perpage)"
                    href=""
                    >{{ i }}
                  </a>
                </li>
                <li v-if="nextpage">
                  <a @click.prevent="getBlogs(nextpage, perpage)"
                    ><i class="fa fa-angle-right"></i
                  ></a>
                </li>
              </ul>
            </div>
            <div v-else></div>
            <!-- Sider Bar -->
            <div class="col-md-3">
              <!-- SEARCH -->
              <div class="search">
                <input
                  class="form-control"
                  type="search"
                  id="title"
                  aria-describedby="name"
                  placeholder="Search"
                  v-model="title"
                  @keyup="search()"
                />
                <button type="submit"><i class="fa fa-search"></i></button>
              </div>
              <div class="shop-sidebar">
                <!-- Category -->
                <h5 class="shop-tittle margin-bottom-30">category</h5>
                <ul>
                  <li
                    class="shop-cate"
                    v-for="category in dataCategory"
                    :key="category.id"
                  >
                    <a @click.prevent="getCategory(category.category)" href="#">
                      {{ category.category }}
                      <span>{{ category.totalCategory }}</span></a
                    >
                  </li>
                </ul>
                <!-- SIDE BACR BANER -->
                <div class="side-bnr margin-top-50">
                  <img
                    class="img-responsive"
                    src="https://images.trademax.se/heminredning-mattor-stora-mattor/stor-matta-nepal-270x356-beigegr%C3%A5-1000360.jpg?w=670&h=447&hash=eyJ2IjowLCJ0IjoicHJvZHVjdCIsIm4iOiI1YzI2MjE5MjU4MWJiM2FkMzgzOTM0MDYzZGI3ZWU3Y2ZmM2Y0Yjg2LmpwZyIsIm9fdHlwZSI6IldFQl9TRTpwcm9kdWN0cyIsIm9faWQiOiIzNjEwMDYiLCJpIjoxMDAwMzYwfQ%3D%3D"
                    alt=""
                  />
                  <div class="position-center-center">
                    <span class="price"><small>$</small>299</span>
                    <div class="bnr-text">look hot with style</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <Instagramfeed />
      <Newsletter />

      <!-- News Letter -->
    </div>
    <Footer />
  </div>
</template>
<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import Banner from "@/components/Banner.vue";
import Newsletter from "@/components/Newsletter.vue";
import Instagramfeed from "@/components/Instagramfeed.vue";

import axios from "axios";

export default {
  name: "About",
  components: {
    Header,
    Banner,
    Footer,
    Instagramfeed,
    Newsletter,
  },
  data() {
    return {
      dataBlog: [],
      dataCategory: [],
      nextpage: "",
      prevpage: "",
      perpage: "",
      total: "",
      from: "",
      name: "",
      currentpage: "",
      path: "",
      title: "",
    };
  },
  mounted() {
    axios
      .get("https://dashboard.sejatistore.my.id/api/blog", {
        params: {
          limit: 5,
        },
      })
      .then((res) => {
        this.dataBlog = res.data.data.data;
        this.nextpage = res.data.data.next_page_url;
        this.prevpage = res.data.data.prev_page_url;
        this.perpage = res.data.data.per_page;
        this.total = Math.ceil(res.data.data.total / res.data.data.per_page);
        this.from = res.data.data.from;
        this.currentpage = res.data.data.current_page;
        this.path = res.data.data.path;
      })
      .catch((err) => console.log(err));

    axios
      .get("https://dashboard.sejatistore.my.id/api/category")
      .then((res) => (this.dataCategory = res.data.data))
      .catch((err) => console.log(err));
  },
  methods: {
    getBlogs(url, limit) {
      axios
        .get(url, {
          params: {
            limit: limit,
          },
        })
        .then((res) => {
          this.dataBlog = res.data.data.data;
          this.nextpage = res.data.data.next_page_url;
          this.prevpage = res.data.data.prev_page_url;
          this.perpage = res.data.data.per_page;
          this.total = Math.ceil(res.data.data.total / res.data.data.per_page);
          this.from = res.data.data.from;
          this.currentpage = res.data.data.current_page;
          this.path = res.data.data.path;
        })
        .catch((err) => console.log(err));
    },
    search() {
      axios
        .get("https://dashboard.sejatistore.my.id/api/blog", {
          params: {
            limit: 5,
            title: this.title,
          },
        })
        .then((res) => {
          this.dataBlog = res.data.data.data;
          this.nextpage = res.data.data.next_page_url;
          this.prevpage = res.data.data.prev_page_url;
          this.perpage = res.data.data.per_page;
          this.total = Math.ceil(res.data.data.total / res.data.data.per_page);
          this.from = res.data.data.from;
          this.currentpage = res.data.data.current_page;
          this.path = res.data.data.path;
        })
        .catch((err) => console.log(err));
    },
    getCategory(name) {
      axios
        .get("https://dashboard.sejatistore.my.id/api/blog", {
          params: {
            category: name,
          },
        })
        .then((res) => {
          this.dataBlog = res.data.data.data;
          this.nextpage = res.data.data.next_page_url;
          this.prevpage = res.data.data.prev_page_url;
          this.perpage = res.data.data.per_page;
          this.total = Math.ceil(res.data.data.total / res.data.data.per_page);
          this.from = res.data.data.from;
          this.currentpage = res.data.data.current_page;
          this.path = res.data.data.path;
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style scoped>
</style>
