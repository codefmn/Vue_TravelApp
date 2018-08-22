<template>
  <div class="header">
    <div class="header-left"><div class="icon-arrow-left2"></div></div>
    <div class="header-input"><i class="icon-search"></i> Input to search</div>
    <router-link to="/city">
      <div class="header-right">{{this.city}} <i class="icon-circle-down"></i></div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  props: {
    city: String
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
      .icon-arrow-left2
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
      text-align center
      width 1.24rem
</style>
