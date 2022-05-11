<template>

  <div>

    <section class="banner-section banner-one">
      <div class="left-based-text">
        <div class="base-inner">
          <div class="hours">
            <ul class="clearfix">
            </ul>
          </div>
        </div>
      </div>

      <div class="banner-carousel">

        <no-ssr> <!-- important to add no-ssr-->
          <carousel :items="1">
        <!-- Slide Item -->
        <div class="slide-item">
          <div class="image-layer" style="background-image: url(/images/main-slider/1.jpg);"></div>
          <div class="left-top-line"></div>
          <div class="right-bottom-curve"></div>
          <div class="right-top-curve"></div>
          <div class="auto-container">
            <div class="content-box">
              <div class="content">
                <div class="inner">
                  <h1 style="color:#ff7f00">Rick And<br>Morty</h1>
                  <div class="link-box">
                    <nuxt-link class="theme-btn btn-style-one" to="/blog-grid">
                      <i class="btn-curve"></i>
                      <span class="btn-title">Karakterler ve Özellikleri</span>
                    </nuxt-link>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

          </carousel>
        </no-ssr>

      </div>
    </section>

  </div>

</template>

<script>

  export default {
    name: "Banner",
  }
</script>

<style scoped>

</style>
