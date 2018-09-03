<template>
  <div>
    <router-link
      tag="div"
      to="/"
      class="header-back"
      v-show="!showFixed"
    >
      <i class="icon-undo"></i>
    </router-link>
    <div
      class="header-fixed"
      v-show="showFixed"
      :style="opacityStyle"
    >
      <router-link to="/">
        <div class="icon-undo"></div>
      </router-link>
      景点门票
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showFixed: false,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacityValue = top / 140
        opacityValue = opacityValue > 1 ? 1 : opacityValue
        this.opacityStyle = { opacity: opacityValue }
        this.showFixed = true
      } else {
        this.showFixed = false
      }
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'
@import '~@/assets/styles/mixins.styl'
.header-back
  background rgba(0,0,0,0.6)
  border-radius .35rem
  color #fff
  font-size .4rem
  padding .15rem
  position absolute
  top .2rem
  left .2rem
.header-fixed
  background $bgColor
  color #fff
  font-size .4rem
  height .9rem
  line-height .9rem
  text-align center
  position fixed
  left 0
  right 0
  top 0
  z-index 2
  .icon-undo
    position absolute
    color #fff
    font-size .4rem
    float left
    margin .2rem .1rem
    width .64rem
</style>
