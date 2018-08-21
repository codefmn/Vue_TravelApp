<template>
  <div class="wrapper">
    <swiper :options="swiperOption" v-if="show">
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl"/>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    swiperList: Array
  },
  data () {
    return {
      swiperOption: {
        autoplay: 3000,
        loop: true,
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    show () {
      return this.swiperList.length
    }
  }
}
</script>

<style lang='stylus' scoped>
@import '~@/assets/styles/mixins.styl'
.wrapper >>> .swiper-pagination-bullet-active
  background: #fff
.wrapper
  background: #eee
  padding-bottom: 24.53%
  HeightZero()
  .swiper-img
    width: 100%
</style>
