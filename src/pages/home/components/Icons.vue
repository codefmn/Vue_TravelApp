<template>
  <div class="wrapper">
    <swiper>
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
  data () {
    return ({
      iconList: [{
        id: '001',
        imgUrl: 'https://img1.doubanio.com/view/photo/l/public/p2531283808.jpg',
        desc: '机票机票机票机票机票'
      }, {
        id: '002',
        imgUrl: 'https://img3.doubanio.com/view/photo/l/public/p2531283805.jpg',
        desc: '风景'
      }, {
        id: '003',
        imgUrl: 'https://img1.doubanio.com/view/photo/l/public/p2531283808.jpg',
        desc: '机票'
      }, {
        id: '004',
        imgUrl: 'https://img3.doubanio.com/view/photo/l/public/p2531283805.jpg',
        desc: '风景'
      }, {
        id: '005',
        imgUrl: 'https://img1.doubanio.com/view/photo/l/public/p2531283808.jpg',
        desc: '机票'
      }, {
        id: '006',
        imgUrl: 'https://img3.doubanio.com/view/photo/l/public/p2531283805.jpg',
        desc: '风景'
      }, {
        id: '007',
        imgUrl: 'https://img1.doubanio.com/view/photo/l/public/p2531283808.jpg',
        desc: '机票'
      }, {
        id: '008',
        imgUrl: 'https://img3.doubanio.com/view/photo/l/public/p2531283805.jpg',
        desc: '风景'
      }, {
        id: '009',
        imgUrl: 'https://img3.doubanio.com/view/photo/l/public/p2531283805.jpg',
        desc: '风景'
      }]
    })
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
