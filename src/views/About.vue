<template>
  <div class="about">
    <Header />
    <Banner :tbanner="'About Us'" />

    <div id="content">
      <!-- History -->
      <section class="history-block padding-top-100 padding-bottom-100">
        <div class="container">
          <div class="row">
            <div class="col-xs-10 center-block">
              <div class="vision-text">
                <div class="col-lg-5">
                  <h5 class="text-left">Tujuan Kami</h5>
                  <h2>Memberikan mutu dan harga yang pantas</h2>
                </div>
                <div class="col-lg-7">
                  <p>
                    Berdiri tahun 2019 dengan niat memajukan minat masyarakat untuk belanja Online melalui jalur yang paling aman yaitu COD, sejati store hadir menjadi salah satu toko online terpercaya untuk kebutuhan rumah tangga dan alat perkakas . Kualitas, harga, dan jangkauan menjadi tiga tujuan kami berada di tengah persaingan online shope Indonesia
                    <br />
                    <br />Dan bagi para reseller maupun dropshipper yang ingin bergabung dengan kami, kami akan siapkan juga mitra Ninja COD sebagai pendukung kalian dalam berjualan selain barang yang murah. Ninja Express menjadi salah satu jasa pengiriman besar di Indonesia
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- OUR TEAM -->
      <section class="our-team light-gray-bg padding-top-150 padding-bottom-100">
        <div class="container">
          <div class="heading text-center">
            <h4>Tim Kami</h4>
          </div>

          <!-- TEAM -->
          <ul class="row">
            <!-- Member -->
            <li class="col-md-4 text-center animate fadeInUp" data-wow-delay="0.4s">
              <article>
                <!-- abatar -->
                <div class="avatar">
                  <img class="img-circle" v-bind:src="'/images/afan.jpg'" alt />
                  <!-- Team hover -->
                  <div class="team-hover">
                    <div class="position-center-center">
                      <div class="social-icons">
                        <a href="https://www.facebook.com/afan.fandiari.7">
                          <i class="icon-social-facebook"></i>
                        </a>
                        <a href="#.">
                          <i class="icon-social-twitter"></i>
                        </a>
                        <a href="#.">
                          <i class="icon-social-dribbble"></i>
                        </a>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- Team Detail -->
                <div class="team-names">
                  <h6>AFAN FANDIARI</h6>
                  <p>CEO & FOUNDER</p>
                </div>
              </article>
            </li>

            <!-- Member -->
            <li class="col-md-4 text-center animate fadeInUp" data-wow-delay="0.6s">
              <article>
                <!-- abatar -->
                <div class="avatar">
                  <img class="img-circle" v-bind:src="'/images/miftah.jpg'" alt />
                  <!-- Team hover -->
                  <div class="team-hover">
                    <div class="position-center-center">
                      <div class="social-icons">
                        <a href="https://www.facebook.com/endutentumifta.fadiah">
                          <i class="icon-social-facebook"></i>
                        </a>
                        <a href="#.">
                          <i class="icon-social-twitter"></i>
                        </a>
                        <a href="#.">
                          <i class="icon-social-dribbble"></i>
                        </a>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- Team Detail -->
                <div class="team-names">
                  <h6>Mifta Fadiah</h6>
                  <p>Marketing</p>
                </div>
              </article>
            </li>
          </ul>
        </div>
      </section>

      <!-- WORK WITH US -->
      <section class="our-team padding-top-150 padding-bottom-100">
        <div class="container">
          <div class="heading text-center">
            <h4>We work with the best</h4>
            <span>We are proud that we have awesome sponsors</span>
          </div>
          <ul class="clients-img">
            <li>
              <img
                class="img-responsive"
                src="https://3.bp.blogspot.com/-JgE5OIyHWzk/W_YcheR36ZI/AAAAAAAAQLM/nBKvNQKz7wwYYtZTBYzMZUAMyRO12PSjQCLcBGAs/s1600/Ninja%2BXpress.png"
                alt
              />
            </li>
          </ul>
        </div>
      </section>

      <!-- About -->
      <section class="small-about padding-top-150 padding-bottom-150">
        <div class="container">
          <!-- Main Heading -->
          <div class="heading text-center">
            <h4>Cari lebih di social media kami</h4>
            <p>Untuk mengetahui semua kegiata kami dan promo menarik bagi dropshipper dan pembeli bisa langsung cek di social media kami dibawah ini</p>
          </div>

          <!-- Social Icons -->
          <ul class="social_icons">
            <li>
              <a href="#.">
                <i class="icon-social-facebook"></i>
              </a>
            </li>
            <li>
              <a href="#.">
                <i class="icon-social-twitter"></i>
              </a>
            </li>
            <li>
              <a href="#.">
                <i class="icon-social-tumblr"></i>
              </a>
            </li>
            <li>
              <a href="#.">
                <i class="icon-social-youtube"></i>
              </a>
            </li>
            <li>
              <a href="#.">
                <i class="icon-social-dribbble"></i>
              </a>
            </li>
          </ul>
        </div>
      </section>
    </div>

    <Footer />
  </div>
</template>
<script>
import Header from "@/components/Header.vue";
import Footer from "@/components/Footer.vue";
import Banner from "@/components/Banner.vue";

export default {
  name: "About",
  components: {
    Header,
    Banner,
    Footer,
  },
};
</script>

<style scoped>
</style>
