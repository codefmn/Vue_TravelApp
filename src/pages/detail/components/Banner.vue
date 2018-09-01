<template>
  <div class="banner">
    <img :src="bannerImg" alt="banner">
    <div class="banner-title">{{sightName}}</div>
  </div>
</template>

<script>
export default {
  name: 'DetailBanner',
  props: {
    bannerImg: String,
    sightName: String
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
    background-image linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 1))
    color #fff
    font-size .3rem
    padding .2rem
    PositionZeroBottom()
</style>
