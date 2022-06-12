<template>
  <ul class="list" ref="listRef">
    <li class="item"
        v-for="(item, key) of cities"
        :key="key"
        :ref="key"
        @touchstart="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
        @click="handleLetterClick(key)"
    >{{ key }}</li>
    </ul>
</template>
<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  computed: {
    letters () {
      const letters = []
      for (let key in this.cities) {
        letters.push(key)
      }
      return letters
    }
  },
  watch: {
    touchLetter () {
      this.$bus.$emit('change-letter', this.touchLetter)
    }
  },
  data () {
    return {
      touchStatus: false,
      touchLetter: '',
      elementY: 0,
      startY: 0,
      listOffsetTop: 0,
      timer: null
    }
  },
  updated () {
    this.elementY = this.$refs['A'][0].offsetHeight
    this.startY = this.$refs['A'][0].offsetTop
    this.listOffsetTop = this.$refs['listRef'].offsetTop
  },
  methods: {
    handleLetterClick (key, e) {
      this.$bus.$emit('change-letter', key)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        // 函数节流
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY
          let touchLetterIdx = Math.floor((touchY - this.listOffsetTop - this.startY) / this.elementY)
          if (touchLetterIdx >= this.letters.length) {
            touchLetterIdx = this.letters.length - 1
          } else if (touchLetterIdx < 0) {
            touchLetterIdx = 0
          }
          this.touchLetter = this.letters[touchLetterIdx]
        }, 8)
      }
    },
    handleTouchEnd (key) {
      this.touchStatus = false
    }
  }
}
</script>
<style lang="stylus" scoped>
@import "~%styles/varibles.styl"
.list
  display flex
  flex-direction column
  justify-content center
  position absolute
  right 0
  top 1.58rem
  bottom 0
  width .4rem
  .item
    line-height .4rem
    text-align center
    color $bgColor
</style>
