<template>
  <div class="banner">
    <!--======= SUB BANNER =========-->
    <section class="sub-bnr" data-stellar-background-ratio="0.5">
      <div class="position-center-center">
        <div class="container">
          <h3 class="text-white">{{tbanner}}</h3>
          <!-- <p>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec faucibus maximus vehicula.
            Sed feugiat, tellus vel tristique posuere, diam
          </p>
          <ol class="breadcrumb">
            <li>
              <a href="#">Home</a>
            </li>
            <li class="active">Data</li>
          </ol>-->
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Banner",
  props: ["tbanner"],
};
</script>