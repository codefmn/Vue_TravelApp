<template>
  <div class="recommend">
    <p class="title">热门推荐</p>
    <ul>
      <router-link
        tag="li"
        class="item border-bottom"
        v-for="item of recommendList"
        :key="item.id"
        :to="'/detail/' + item.id"
      >
        <img :src="item.imgUrl" alt="recommend">
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button>详细信息</button>
        </div>
      </router-link>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Recommend',
  props: {
    recommendList: Array
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
  display flex
  height 1.9rem
  img
    padding .1rem
    height 1.7rem
    width 1.7rem
  .item-info
    padding .1rem
    min-width 0
    .item-title
      font-size .35rem
      line-height .5rem
    .item-desc
      color #999
      line-height .5rem
      Ellipsis()
    button
      background #ff9900
      border-radius .1rem
      color #fff
      line-height .3rem
      margin-top .1rem
      padding .1rem
</style>
