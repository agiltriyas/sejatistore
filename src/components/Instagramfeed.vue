<template>
  <div class="instagramfeed">
    <!-- Culture BLOCK -->
    <section class="cultur-block">
      <!-- <ul v-if="dataInsta.length > 0">
        <carousel
          :nav="false"
          :dots="false"
          class="product-thumbs-track ps-slider"
        >
          <li v-for="insta in dataInsta" :key="insta.id">
            <a :href="insta.permalink" target="_blank">
              <img :src="insta.media_url" alt="" />
            </a>
          </li> -->
      <ul>
        <carousel
          :nav="false"
          :dots="false"
          :autoplay="true"
          :loop="true"
          :items="4"
          :autoplayHoverPause="true"
          :responsive="{ 480: { items: 2 }, 767: { items: 4 } }"
          class="insta"
        >
          <li>
            <img src="https://placeimg.com/475/445/any?1" />
          </li>
          <li>
            <img src="https://placeimg.com/475/445/any?2" />
          </li>
          <li>
            <img src="https://placeimg.com/475/445/any?3" />
          </li>
          <li>
            <img src="https://placeimg.com/475/445/any?4" />
          </li>
          <li>
            <img src="https://placeimg.com/475/445/any?5" />
          </li>
          <li>
            <img src="https://placeimg.com/475/445/any?6" />
          </li>
          <li>
            <img src="https://placeimg.com/475/445/any?7" />
          </li>
          <li>
            <img src="https://placeimg.com/475/445/any?8" />
          </li>
        </carousel>
      </ul>
      <!-- Culture Text -->
      <div class="position-center-center" style="z-index: 999999">
        <div class="container">
          <div class="col-sm-6 center-block">
            <h4>FOLLOW US @ INSTAGRAM</h4>
            <p>
              Untuk mendapatkan produk dan promo terupdate bisa cek instagram
              kita guys dan sista.
            </p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
import carousel from "vue-owl-carousel";
import axios from "axios";

export default {
  name: "Instagramfeed",
  components: {
    carousel,
  },
  data() {
    return {
      dataInsta: [],
    };
  },
  mounted() {
    axios
      .get(
        "https://graph.instagram.com/17841400925500697/media?fields=id&access_token=aaIGQVJYS2RBQlpyOVpSUldMdkdyOVktMTVOenNlSXlNWGxmUHBOWExwTkpTa3NzOUk3dHJfek80dy1LTGlmVlRjNERUNm1ZAS2MwRnNuZAGRwSmFaY3hoWERFdGYzcURqQmtkVnB0dWhn",
        {
          params: {
            limit: 8,
          },
        }
      )
      .then((res) => this.getId(res.data.data))
      .catch((err) => console.log(err));
  },
  methods: {
    getId(id) {
      for (let index = 0; index < 8; index++) {
        axios
          .get(
            "https://graph.instagram.com/" +
              id[index].id +
              "?fields=media_url,permalink&access_token=aaIGQVJYS2RBQlpyOVpSUldMdkdyOVktMTVOenNlSXlNWGxmUHBOWExwTkpTa3NzOUk3dHJfek80dy1LTGlmVlRjNERUNm1ZAS2MwRnNuZAGRwSmFaY3hoWERFdGYzcURqQmtkVnB0dWhn"
          )
          .then((res) => this.dataInsta.push(res.data))
          .catch((err) => console.log(err));
      }
    },
  },
};
</script>

<style scoped>
/* .logo img {
  width: 40%;
} */
.insta {
  z-index: -9999;
}
@media (min-width: 992px) and (max-width: 1199px) {
  .insta li img {
    width: 25vw;
  }
}
/* Tablets portrait and small desktops*/
@media (min-width: 768px) and (max-width: 991px) {
  .insta li img {
    width: 25vw;
  }
}
/* landscape phones and portrait tablets */
@media (max-width: 767px) {
  .insta li img {
    width: 48vw;
  }
}
/* landscape phones and small devices */
@media (max-width: 480px) {
  .insta li img {
    width: 50vw;
  }
}

@media (min-width: 1200px) {
  .insta li img {
    width: 25vw;
  }
}
</style>