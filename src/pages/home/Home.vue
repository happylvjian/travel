<template>
  <div>
    <home-header></home-header>
    <home-swiper></home-swiper>
    <div ><span class="text-test">test</span></div>
  </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper
  }
}
</script>
<style lang="stylus" scoped>
</style>
