<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(page, index) of pages" :key="index">
        <div class="icon" v-for="item of page" :key="item.id">
            <img :src="item.imgUrl">
            <p>{{item.desc}}</p>
        </div>
      </swiper-slide>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    iconList: Array
  },
  data () {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.styl'
.wrapper >>> .swiper-container
  padding-bottom: 50%
  HeightZero()
.icon
  float: left
  height: 0
  padding-bottom: 25%
  position: relative
  width: 25%
  img
    box-sizing: border-box
    height: 80%
    padding: 5%
    margin: 0 auto
    PositionZeroTop()
  p
    color: #333
    height: 20%
    text-align: center
    PositionZeroBottom()
    Ellipsis()
</style>
