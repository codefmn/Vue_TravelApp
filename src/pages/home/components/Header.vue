<template>
  <div class="header">
    <div class="header-left"><div class="icon-arrow-left2"></div></div>
    <div class="header-input"><i class="icon-search"></i> Input to search</div>
    <div class="header-right">{{this.city}} <i class="icon-circle-down"></i></div>
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
    background-color: $bgColor
    color: #fff
    display: flex
    line-height: .86rem
    .header-left
      width: .64rem
      float: left
      .icon-arrow-left2
        font-size: .4rem
        margin: .2rem .1rem
    .header-input
      background-color: #fff
      border-radius: .1rem
      color: #ccc
      flex: 1
      line-height: .64rem
      margin: .12rem 0
      padding-left: .2rem
    .header-right
      width: 1.24rem
      float: right
      text-align: center
</style>
