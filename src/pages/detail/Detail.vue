<template>
  <div>
    <detail-banner
      :bannerImg="bannerImg"
      :sightName="sightName"
      :galleryImgs="galleryImgs"
    ></detail-banner>
    <detail-header></detail-header>
    <detail-list :categoryList="categoryList"></detail-list>
    <div class="blank"></div>
  </div>
</template>

<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailList,
    DetailHeader
  },
  data () {
    return {
      bannerImg: '',
      sightName: '',
      galleryImgs: [],
      categoryList: []
    }
  },
  mounted () {
    axios.get('https://www.easy-mock.com/mock/5b8ec1bb9125da0e4952ad30/travel/detail', {
      params: {
        id: this.$route.params.id
      }
    })
      .then(response => response.data)
      .then(response => {
        if (response.ret && response.data) {
          this.bannerImg = response.data.bannerImg
          this.sightName = response.data.sightName
          this.galleryImgs = response.data.galleryImgs
          this.categoryList = response.data.categoryList
        }
      })
  }
}
</script>

<style lang="stylus" scoped>
.blank
  height 30rem
</style>
