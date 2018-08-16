<template>
  <div class="header">
    <div class="header-left">back</div>
    <div class="header-input">input</div>
    <div class="header-right">city</div>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader'
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
    .header-input
      background-color: #fff
      border-radius: .1rem
      color: #ccc
      flex: 1
      line-height: .64rem
      margin: .12rem 0
    .header-right
      width: 1.24rem
      float: right
      text-align: center
</style>
