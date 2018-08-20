<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
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
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperList: [{
        id: '001',
        imgUrl: 'http://img2.ph.126.net/pTABtg17j7nRDZX6Vdh6Kw==/6631646108819674574.png'
      }, {
        id: '002',
        imgUrl: 'http://img2.ph.126.net/_E0VAB0Fb6-bR9K5QUNxag==/6632745620444886572.png'
      }]
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
