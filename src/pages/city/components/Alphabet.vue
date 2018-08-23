<template>
  <ul class="list">
    <li v-for="(item,key) of cities" :key="key">{{key}}</li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'
.list
  display flex
  flex-direction column
  justify-content center
  padding .15rem
  position absolute
  top 2rem
  right 0
  bottom 0
  li
    color $bgColor
    line-height .4rem
</style>
