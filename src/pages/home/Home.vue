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
import { mapState } from 'vuex'
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
      lastCity: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getInfo () {
      axios.get('https://www.easy-mock.com/mock/5b8ec1bb9125da0e4952ad30/travel/index?city=' + this.city)
        .then(response => response.data)
        .then(response => {
          if (response.ret && response.data) {
            this.swiperList = response.data.swiperList
            this.iconList = response.data.iconList
            this.recommendList = response.data.recommendList
            this.weekendList = response.data.weekendList
          }
        })
        .catch(error => alert(error.message))
    }
  },
  mounted () {
    this.lastCity = this.city
    this.getInfo()
  },
  activated () {
    if (this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getInfo()
    }
  }
}
</script>

<style>

</style>
