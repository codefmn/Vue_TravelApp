<template>
  <div>
    <detail-banner
      :bannerImg="bannerImg"
      :sightName="sightName"
      :galleryImgs="galleryImgs"
    ></detail-banner>
  </div>
</template>

<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
export default {
  name: 'Detail',
  components: {
    DetailBanner
  },
  data () {
    return {
      bannerImg: '',
      sightName: '',
      galleryImgs: []
    }
  },
  mounted () {
    axios.get('api/detail.json')
      .then(response => response.data)
      .then(response => {
        if (response.ret && response.data) {
          this.bannerImg = response.data.bannerImg
          this.sightName = response.data.sightName
          this.galleryImgs = response.data.galleryImgs
        }
      })
  }
}
</script>
