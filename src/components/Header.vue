<template>
  <div class="header">
    <header>
      <div class="sticky">
        <div class="container">
          <!-- Logo -->
          <div class="logo">
            <router-link to="/">
              <img class="img-responsive" v-bind:src="'/images/LogoSejatistore.png'" alt />
            </router-link>
          </div>
          <nav class="navbar ownmenu">
            <div class="navbar-header">
              <button
                type="button"
                class="navbar-toggle collapsed"
                data-toggle="collapse"
                data-target="#nav-open-btn"
                aria-expanded="false"
              >
                <span class="sr-only">Toggle navigation</span>
                <span class="icon-bar">
                  <i class="fa fa-navicon"></i>
                </span>
              </button>
            </div>

            <!-- NAV -->
            <div class="collapse navbar-collapse" id="nav-open-btn">
              <ul class="nav">
                <li :class="url == '/' ? 'active' : ''">
                  <router-link to="/">
                    <a href class="dropdown-toggle" data-toggle="dropdown">Home</a>
                  </router-link>
                </li>
                <li :class="url == '/about' ? 'active' : ''">
                  <router-link to="about">
                    <a href>about</a>
                  </router-link>
                </li>
              </ul>
            </div>
          </nav>
        </div>
      </div>
    </header>
  </div>
</template>
<script>
export default {
  name: "Header",
  data() {
    return {
      url: this.$route.path,
    };
  },
};
</script>

<style>
/* .logo img {
  width: 40%;
} */
</style>