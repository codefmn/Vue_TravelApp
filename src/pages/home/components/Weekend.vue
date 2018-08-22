<template>
  <div class="weekend">
    <p class="title">周末游玩</p>
    <ul>
      <li class="item border-bottom" v-for="item of weekendList" :key="item.id">
        <img :src="item.imgUrl" alt="weekend">
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'weekend',
  props: {
    weekendList: Array
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.styl'
.title
  background #eee
  font-size .4rem
  line-height .8rem
  text-indent .2rem
.item
  height 3rem
  img
    height 60%
    width 100%
  .item-info
    padding .1rem
    .item-title
      font-size .35rem
      line-height .5rem
    .item-desc
      color #999
      line-height .5rem
      Ellipsis()
</style>
