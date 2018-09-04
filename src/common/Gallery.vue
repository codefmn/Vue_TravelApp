<template>
  <fade-animation>
    <div class="gallery" @click="handleGalleryClick">
      <div class="wrapper">
        <swiper :options="swiperOption">
          <swiper-slide v-for="(item,index) of galleryImgs" :key="index">
            <img class="gallery-img" :src="item"/>
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </div>
    </div>
  </fade-animation>
</template>

<script>
import FadeAnimation from './FadeAnimation'
export default {
  name: 'CommonGallery',
  components: {
    FadeAnimation
  },
  props: {
    galleryImgs: Array
  },
  data () {
    return {
      swiperOption: {
        loop: true,
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  methods: {
    handleGalleryClick () {
      this.$emit('close')
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.styl'
.wrapper >>> .swiper-container
  overflow inherit
.gallery
  FlexColumnCenter()
  background #000
  position fixed
  left 0
  right 0
  top 0
  bottom 0
  z-index 99
  .wrapper
    background #fff
    padding-bottom 100%
    height 0
    .gallery-img
      width 100%
    .swiper-pagination
      color #fff
      bottom -1rem
</style>
