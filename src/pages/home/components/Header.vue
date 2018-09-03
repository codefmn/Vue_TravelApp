<template>
  <div class="header">
    <div class="header-left"><div class="icon-undo"></div></div>
    <div class="header-input"><i class="icon-search"></i> Input to search</div>
    <router-link to="/city">
      <div class="header-right">{{this.city}} <i class="icon-circle-down"></i></div>
    </router-link>
  </div>
</template>

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus"  scoped>
  @import '~@/assets/styles/varibles.styl'
  .header
    background-color $bgColor
    color #fff
    display flex
    line-height .9rem
    .header-left
      float left
      width .64rem
      .icon-undo
        font-size .4rem
        margin .2rem .1rem
    .header-input
      background-color #fff
      border-radius .1rem
      color #ccc
      flex 1
      line-height .64rem
      margin .12rem 0
      padding-left .2rem
    .header-right
      color #fff
      float right
      padding 0 .1rem
      text-align center
      min-width 1.2rem
</style>
