<template>
  <div class="blogdetail">
    <Header />
    <div id="content">
      <!-- Blog List -->
      <section
        class="blog-list blog-list-3 single-post padding-top-100 padding-bottom-100"
      >
        <div class="container">
          <div class="row">
            <div class="col-md-9">
              <!-- Article -->
              <article>
                <!-- Post Img -->
                <img class="img-responsive" :src="blogdetail[0].image" alt="" />
                <!-- Tittle -->
                <div class="post-tittle left">
                  <a href="#." class="tittle">{{ blogdetail[0].title }}</a>
                  <!-- Post Info -->
                  <span><i class="primary-color icon-user"></i> by admin</span>
                  <span
                    ><i class="primary-color icon-calendar"></i>
                    {{ blogdetail[0].created_at }}</span
                  >
                  <span
                    ><i class="primary-color icon-tag"></i>
                    {{ blogdetail[0].category }}
                  </span>
                </div>
                <!-- Post Content -->
                <div class="text-left">
                  <p>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Nullam volutpat dui at lacus aliquet, a consequat enim
                    aliquet. Integer molestie sit amet sem et faucibus. Nunc
                    ornare pharetra dui, vitae auctor orci fringilla eget.
                    Pellentesque in placerat felis. Etiam mollis venenatis
                    luctus. Morbi ac scelerisque mauris. Etiam sodales a nulla
                    ornare viverra. Nunc at blandit neque, bibendum varius
                    purus. <br />
                    <br />
                    Nam sit amet sapien vitae enim vehicula tincidunt. Cum
                    sociis natoque penatibus et magnis dis parturient montes,
                    nascetur ridiculus mus. Nunc faucibus imperdiet vulputate.
                    Morbi volutpat leo iaculis elit vehicula, eu convallis magna
                    finibus. Suspendisse tristique ullamcorper erat a elementum.
                    Cras eget elit non nunc aliquam ullamcorper quis sed metus.
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Donec malesuada, erat in ullamcorper bibendum, elit lacus
                    mattis lorem, quis luctus diam lorem vel ligula.
                  </p>
                  <h6 class="margin-top-80 margin-bottom-30">
                    proeduct history
                  </h6>
                  <p>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Nullam volutpat dui at lacus aliquet, a consequat enim
                    aliquet. Integer molestie sit amet sem et faucibus. Nunc
                    ornare pharetra dui, vitae auctor orci fringilla eget.
                    Pellentesque in placerat felis. Etiam mollis venenatis
                    luctus. Morbi ac scelerisque mauris. Etiam sodales a nulla
                    ornare viverra. <br />
                    <br />
                    Nam sit amet sapien vitae enim vehicula tincidunt. Cum
                    sociis natoque penatibus et magnis dis parturient montes,
                    nascetur ridiculus mus. Nunc faucibus imperdiet vulputate.
                    Morbi volutpat leo iaculis elit vehicula, eu convallis magna
                    finibus. Lorem ipsum dolor sit amet, consectetur adipiscing
                    elit. Donec malesuada, erat in ullamcorper bibendum, elit
                    lacus mattis lorem, quis luctus diam lorem vel ligula.
                  </p>

                  <!-- Post Img -->
                  <img
                    class="img-responsive margin-top-50 margin-bottom-50"
                    src="https://placeimg.com/1170/510/any"
                    alt=""
                  />
                  <p>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Nullam volutpat dui at lacus aliquet, a consequat enim
                    aliquet. Integer molestie sit amet sem et faucibus. Nunc
                    ornare pharetra dui, vitae auctor orci fringilla eget.
                    Pellentesque in placerat felis. Etiam mollis venenatis
                    luctus. Morbi ac scelerisque mauris. Etiam sodales a nulla
                    ornare viverra. Nunc at blandit neque, bibendum varius
                    purus. <br />
                    <br />
                    Nam sit amet sapien vitae enim vehicula tincidunt. Cum
                    sociis natoque penatibus et magnis dis parturient montes,
                    nascetur ridiculus mus. Nunc faucibus imperdiet vulputate.
                    Morbi volutpat leo iaculis elit vehicula, eu convallis magna
                    finibus. Suspendisse tristique ullamcorper erat a elementum.
                    Cras eget elit non nunc aliquam ullamcorper quis sed metus.
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Donec malesuada, erat in ullamcorper bibendum, elit lacus
                    mattis lorem, quis luctus diam lorem vel ligula.
                  </p>

                  <!-- LIST STYLE -->
                  <ul class="list-group margin-top-50 margin-top-20">
                    <li>
                      <p>Donec sed dictum leo, et posuere felis.</p>
                    </li>
                    <li>
                      <p>
                        Sed pharetra mauris vel varius suscipit. Aliquam lectus
                        velit,
                      </p>
                    </li>
                    <li>
                      <p>Tempus id est ut, volutpat maximus sapien.</p>
                    </li>
                  </ul>
                  <p>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Nullam volutpat dui aolutpat dui at lacus aliquet, a
                    consequat et lacus aliquet, a consequat enim aliquet.
                    Integer molestie sit ame.
                  </p>

                  <!-- Blockquote -->
                  <blockquote>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    Nullam volutpat dui at lacus aliquet, a consequat enim
                    aliquet. Integer molestie sit amet sem et faucibus.
                  </blockquote>
                  <p>
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                    NullamMorbi ac scelerisque mauris. Etiam sodales a nulla
                    ornare viverra. Nunc at blandit neque, bociis natoque
                    penatibus et magnnascetiscing elit. NullamMorbi ac
                    scelerisque miscing elit. NullamMorbi ac scelerisque mur
                    ridic volutpat dui at lacus aliquet, a consequat enim
                    aliquet. Integer molestie sit ame.
                  </p>
                </div>
              </article>
              <hr />

              <!--  You May Like -->
              <h5 class="shop-tittle margin-top-50 margin-bottom-50">
                you may like
              </h5>
              <div class="alos-like padding-left-15">
                <!-- Article -->
                <article v-if="blogdetailcat.length > 0">
                  <div
                    v-for="blogcat in blogdetailcat"
                    :key="blogcat.id"
                    class="row"
                  >
                    <div class="col-sm-5">
                      <!-- Post Img -->
                      <img
                        class="img-responsive"
                        :src="blogcat.imagethumb"
                        alt=""
                      />
                    </div>
                    <div class="col-sm-7">
                      <!-- Tittle -->
                      <div class="post-tittle left">
                        <a href="#." class="tittle">{{ blogcat.title }}</a>
                        <!-- Post Info -->
                        <span
                          ><i class="primary-color icon-user"></i> by
                          admin</span
                        >
                        <span
                          ><i class="primary-color icon-calendar"></i>
                          {{ blogcat.creted_at }}</span
                        >
                        <span
                          ><i class="primary-color icon-tag"></i>
                          {{ blogcat.category }}</span
                        >
                      </div>
                      <!-- Post Content -->
                      <div class="text-left">
                        <p>
                          {{ blogcat.content }}
                        </p>
                        <router-link
                          :to="'/blog/' + blogcat.slug"
                          class="red-more"
                          >READ MORE</router-link
                        >
                      </div>
                    </div>
                  </div>
                </article>

                <article v-else></article>
              </div>
            </div>
          </div>
        </div>
      </section>

      <Instagramfeed />
      <Newsletter />
    </div>
    <Footer />
  </div>
</template>
<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import Newsletter from "@/components/Newsletter.vue";
import Instagramfeed from "@/components/Instagramfeed.vue";

import axios from "axios";

export default {
  name: "Blogdetail",
  data() {
    return {
      blogdetail: [],
      blogdetailcat: [],
    };
  },
  components: {
    Header,
    Footer,
    Newsletter,
    Instagramfeed,
  },

  mounted() {
    axios
      .get("https://dashboard.sejatistore.my.id/api/blog", {
        params: {
          slug: this.$route.params.slug,
        },
      })
      .then((res) => {
        this.blogdetail = res.data.data;
        this.getCategory(res.data.data);
      })
      .catch((err) => console.log(err));
  },
  methods: {
    getCategory(data) {
      axios
        .get("https://dashboard.sejatistore.my.id/api/blog", {
          params: {
            category: data[0].category,
          },
        })
        .then((res) => (this.blogdetailcat = res.data.data.data))
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style scoped>
</style>
