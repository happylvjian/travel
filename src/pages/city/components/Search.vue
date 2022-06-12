<template>
  <div>
    <div class="search">
      <input v-model="keyword" class="search-input" type="text" placeholder="输入城市名或拼音" />
    </div>
    <div class="search-content" v-show="keyword.length" ref="listWrapper">
      <ul>
        <li
          class="search-item"
          border-bottom
          v-for="item of list"
          :key="item.id"
          @click="handleCityClick(item.name)"
        >{{item.name}}</li>
      </ul>
    </div>
  </div>
</template>
<script>
import BetterScroll from 'better-scroll'
export default {
  name: 'CitySearch',
  components: {
  },
  props: {
    cities: Object
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        let keywordTrim = this.keyword.trim()
        if (keywordTrim) {
          const result = []
          for (let i in this.cities) {
            this.cities[i].forEach((item) => {
              if (item.spell.indexOf(keywordTrim) > -1 ||
                item.name.indexOf(keywordTrim) > -1) {
                result.push(item)
              }
            })
          }
          this.list = result
        } else {
          this.list = []
        }
        this.$nextTick(() => {
          this.bScroll.refresh()
        })
      }, 80)
    }
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null,
      bScroll: undefined
    }
  },
  mounted () {
    this.bScroll = new BetterScroll(this.$refs.listWrapper)
  },
  updated () {

  },
  methods: {
    handleCityClick (city) {
      this.$store.commit('changeCity', city)
      this.keyword = ''
      this.$router.back()
    }
  }
}
</script>
<style lang="stylus" scoped>
@import "~%styles/varibles.styl"
.search
  height .72rem
  background $bgColor
  padding .1rem
  .search-input
    box-sizing border-box
    width 100%
    height .72rem
    padding 0 .1rem
    line-height .72rem
    text-align center
    border-radius .06rem
    color #666
.search-content
  overflow hidden
  position absolute
  z-index 1
  top 1.78rem
  bottom 0
  left 0
  right 0
  background #eee
  .search-item {
    line-height .62rem
    padding-left .2rem
    background #fff
    color #666
  }
</style>
