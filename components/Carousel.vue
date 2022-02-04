<template>

  <Flickity ref="flickity" :options="flickityOptions">
    <img 
      v-for="(item, index) in 10" :key="index" class="carousel-cell card-placeholder"
      :data-flickity-lazyload="`https://picsum.photos/${w_width}/${w_height}?random=${index}`"
    > <!-- The index in img src is meant to get different images from picsum at one call -->
  </Flickity>

</template>

<script>

export default {
  name: 'Carousel',
  data() {
    return {
      flickityOptions: {
        lazyLoad: 10,     // Load the images client side (prevent page reload void)
        wrapAround: true, // Infinite scroll loop
        autoPlay: true,
        freeScroll: true,
        freeScrollFriction: 0.03,
      },
      // Images Scale settings for picsum API
      w_height: 1080,
      w_width: 1920,
      loading: true,
    }
  },

  mounted() {
    this.on_resize() // First resize if the original scale isn't 1920x1080

    this.$nextTick(() => {
      window.addEventListener('resize', this.on_resize);
    })
  },

  beforeDestroy() { 
    window.removeEventListener('resize', this.on_resize); 
  },

  methods: {
    next() {
      this.$refs.flickity.next();
    },
    
    previous() {
      this.$refs.flickity.previous();
    },

    on_resize() {
      this.loading = true
      // Update picsum images settings
      this.w_height = window.innerHeight
      this.w_width = window.innerWidth
      // The Next tick will trigger the lazyLoad from flickity and get images
      // accurates with the new settings.
      this.loading = false
    }
  }
}
</script>

<style lang="scss">
  /* full width and height cells */
  .carousel-cell {
    width: 100%;
    height: 98vh;
    margin-right: 10px;
  }

  /* position dots in carousel */
  .flickity-page-dots { 
    bottom: 20px !important; 
  }

  /* white circles */
  .flickity-page-dots .dot {
    width: 13px !important;
    height: 13px !important;
    margin: 8px !important;
    opacity: 0.80 !important;
    background: transparent;
    border: 2px solid white;
  }
  /* fill-in selected dot */
  .flickity-page-dots .dot.is-selected {
    background: white;
  }

  @media screen and ( min-width: 768px ) {
    .carousel-cell { width: 90%; }
  }
</style>