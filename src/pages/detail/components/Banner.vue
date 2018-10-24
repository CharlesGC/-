<template>
    <div class="banner">
      <img class="banner-img" :src="bannerImg" alt="" @click="bannerClick"/>
      <div class="banner-info">
        <div class="banner-title">
          {{this.sightName}}
        </div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe674;</span>
          {{this.gallaryImgs.length}}
        </div>
      </div>
      <common-gallary :imgs="gallaryImgs" v-show="showGallary" @close="gallaryClose"></common-gallary>
    </div>
</template>

<script>
import CommonGallary from '@/common/gallary/Gallary'
export default {
  name: 'Banner',
  props: {
    bannerImg: String,
    sightName: String,
    gallaryImgs: Array
  },
  data () {
    return {
      showGallary: false
    }
  },
  components: {
    CommonGallary
  },
  methods: {
    bannerClick () {
      this.showGallary = true
    },
    gallaryClose () {
      this.showGallary = false
    }
  }
}
</script>

<style scoped lang="stylus">
  .banner
    position: relative
    overflow: hidden
    height: 0
    padding-bottom: 55%
    .banner-img
      width: 100%
    .banner-info
      display: flex
      position: absolute
      left: 0
      right: 0
      bottom: 0
      line-height: .6rem
      color: #fff
      padding 0 .1rem
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
      .banner-tittle
        flex: 1
        font-size: .32rem
        padding: 0 .2rem
      .banner-number
        height: .32rem
        line-height: .32rem
        margin-top: .14rem
        padding: 0 .4rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .8)
        font-size: .24rem
        position absolute
        right 0.1rem
        .banner-icon
          font-size: .24rem
</style>
