<template>
  <div>
      <home-header :city="city"></home-header>
      <home-swiper :swiperList="swiperList"></home-swiper>
      <home-icons :iconList="iconList"></home-icons>
  </div>
</template>

<script>
import axios from 'axios'
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons
  },
  data () {
    return {
      city: '',
      swiperList: [],
      iconList: []
    }
  },
  mounted () {
    axios.get('/api/index.json')
      .then(response => response.data)
      .then((response) => {
        if (response.ret && response.data) {
          this.city = response.data.city
          this.swiperList = response.data.swiperList
          this.iconList = response.data.iconList
        }
        console.log(response)
      })
  }
}
</script>

<style>

</style>
