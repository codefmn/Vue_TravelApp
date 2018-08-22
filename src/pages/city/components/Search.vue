<template>
  <div class="search">
    <input type="text" placeholder="请输入城市名或拼音">
  </div>
</template>

<script>
export default {
  name: 'CitySearch'
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'
.search
  background $bgColor
  height .7rem
  padding .2rem
  input
    border-radius .1rem
    box-sizing border-box
    line-height .65rem
    text-align center
    padding 0 .2rem
    width 100%
</style>
