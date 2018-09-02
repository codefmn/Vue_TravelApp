<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img :src="bannerImg" alt="banner">
      <div class="banner-title">{{sightName}} （点击查看大图）</div>
    </div>
    <common-gallery
      @close="handleGalleryClose"
      v-show="showGallery"
      :galleryImgs="galleryImgs"
    ></common-gallery>
  </div>
</template>

<script>
import CommonGallery from '@/common/Gallery'
export default {
  name: 'DetailBanner',
  components: {
    CommonGallery
  },
  props: {
    bannerImg: String,
    sightName: String,
    galleryImgs: Array
  },
  data () {
    return {
      showGallery: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallery = true
    },
    handleGalleryClose () {
      this.showGallery = false
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.styl'
.banner
  HeightZero()
  padding-bottom 55%
  position relative
  img
    width 100%
  .banner-title
    background-image linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 1))
    color #fff
    font-size .3rem
    padding .2rem
    PositionZeroBottom()
</style>
