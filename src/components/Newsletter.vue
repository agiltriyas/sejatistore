<template>
  <div class="newsletter">
    <section class="news-letter padding-top-150 padding-bottom-150">
      <div class="container">
        <div class="heading light-head text-center margin-bottom-30">
          <h4>NEWSLETTER</h4>
          <span
            >Untuk mendapatkan update produk baru dan promosi segera
            berlangganan melalu email
          </span>
        </div>
        <form>
          <input
            type="email"
            id="email"
            placeholder="Enter your email address"
            v-model="email"
            required
          />
          <button type="button" @click.prevent="postEmail()">SEND ME</button>
        </form>
      </div>
    </section>
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "Newsletter",
  data() {
    return {
      email: "",
    };
  },
  methods: {
    postEmail() {
      let dataEmail = {
        email: this.email,
      };
      axios
        .post("https://dashboard.sejatistore.my.id/api/subscription", dataEmail)
        .then(() => this.$router.push("../success"))
        .catch((err) => console.log(err));

      console.log(dataEmail);
    },
  },
};
</script>

<style>
/* .logo img {
  width: 40%;
} */
</style>