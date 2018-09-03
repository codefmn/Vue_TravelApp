<template>
  <div>
    <div
      class="item border-topbottom"
      tag="li"
      v-for="(item,index) of categoryList"
      :key="index"
    >
      <i class="item-icon icon-ticket"></i>
      {{item.title}}
      <div class="item-children" v-if="item.children">
        <detail-list :categoryList="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    categoryList: Array
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'
.item
  font-size .4rem
  line-height .6rem
  padding 0 .2rem
  .item-icon
    background $bgColor
    border-radius .17rem
    color #fff
  .item-children
    padding 0 .2rem
</style>
