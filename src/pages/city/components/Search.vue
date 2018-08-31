<template>
  <div>
    <div class="search">
      <input
        v-model="keyword"
        type="text"
        placeholder="请输入城市名或拼音"
      >
    </div>
    <div
      class="search-result"
      ref="result"
      v-show="keyword"
    >
      <ul>
        <li
          class="result-item border-bottom"
          v-for="item of resultList"
          :key="item.id"
          @click="handleCityClick(item.name)"
        >
        {{item.name}}
        </li>
        <li
          class="result-item border-bottom"
          v-show="!resultList.length"
        >
          没有找到匹配城市
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
import { mapMutations } from 'vuex'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      resultList: [],
      timer: null
    }
  },
  methods: {
    handleCityClick (city) {
      // this.$store.commit('changeCity', city)
      this.changeCity(city)
      this.$router.push('/')
    },
    ...mapMutations(['changeCity'])
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.resultList = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let key in this.cities) {
          this.cities[key].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 ||
            value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.resultList = result
      }, 100)
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.result)
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'
@import '~@/assets/styles/mixins.styl'
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
.search-result
  background #eee
  overflow hidden
  top 2rem
  PositionZeroBottom()
  z-index 1
  .result-item
    background #fff
    padding .1rem
    text-indent .2rem
</style>
