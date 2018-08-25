<template>
  <div class="list" ref="wrapper">
    <div>
      <div class="area">
        <p class="title border-topbottom">当前城市</p>
        <div class="button-list">
          <button type="button">{{this.$store.state.city}}</button>
        </div>
      </div>
      <div class="area">
        <p class="title border-topbottom">热门城市</p>
        <div class="button-list">
          <button
            v-for="item of hotCities"
            :key="item.id"
            @click="handleCityClick(item.name)"
          >
            {{item.name}}
          </button>
        </div>
      </div>
      <div
        class="area"
        v-for="(item,key) of cities"
        :key="key"
        :ref="key"
      >
        <p class="title border-topbottom">{{key}}</p>
        <ul class="item-list">
          <li
            class="border-bottom"
            v-for="innerItem of item"
            :key="innerItem.id"
            @click="handleCityClick(innerItem.name)"
          >
            {{innerItem.name}}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CityList',
  props: {
    hotCities: Array,
    cities: Object,
    letter: String
  },
  methods: {
    handleCityClick (city) {
      this.$store.commit('changeCity', city)
      this.$router.push('/')
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.styl'
.border-topbottom
  &:after
    border-color #999
  &:before
    border-color #999
.border-bottom
  &:before
    border-color #ccc
.list
  overflow hidden
  top 2rem
  PositionZeroBottom()
  .title
    background #eee
    line-height .45rem
    text-indent .2rem
  .button-list
    padding .1rem .5rem .1rem .1rem
    button
      background #fff
      border: .03rem solid #ccc
      border-radius .15rem
      margin .1rem
      padding .05rem
      width 29%
  .item-list
    li
      text-indent .2rem
      line-height .6rem
</style>
