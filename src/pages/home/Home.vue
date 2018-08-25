<template>
  <div>
      <home-header></home-header>
      <home-swiper :swiperList="swiperList"></home-swiper>
      <home-icons :iconList="iconList"></home-icons>
      <home-recommend :recommendList="recommendList"></home-recommend>
      <home-weekend :weekendList="weekendList"></home-weekend>
  </div>
</template>

<script>
import axios from 'axios'
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  data () {
    return {
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  mounted () {
    axios.get('/api/index.json')
      .then(response => response.data)
      .then(response => {
        if (response.ret && response.data) {
          this.swiperList = response.data.swiperList
          this.iconList = response.data.iconList
          this.recommendList = response.data.recommendList
          this.weekendList = response.data.weekendList
        }
        console.log(response)
      })
      .catch(error => alert(error.message))
  }
}
</script>

<style>

</style>
