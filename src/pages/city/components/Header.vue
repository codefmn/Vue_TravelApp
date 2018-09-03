<template>
  <div class="header">
    <router-link to="/">
      <div class="header-left"><div class="icon-undo"></div></div>
    </router-link>
    城市选择
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'
.header
  background $bgColor
  color #fff
  font-size .4rem
  height .9rem
  line-height .9rem
  text-align center
  .icon-undo
    position absolute
    color #fff
    font-size .4rem
    float left
    margin .2rem .1rem
    width .64rem
</style>
