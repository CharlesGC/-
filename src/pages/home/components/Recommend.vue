<template>
  <div>
    <div class="title">
      猜你喜欢
    </div>
    <ul>
      <li class="item border-bottom" v-for="item of recommendList" :key="item.id">
        <img class="item-img" :src="item.imgUrl" alt="">
        <div class="item-info">
          <p class="item-title">{{item.title}}</p>
          <p class="item-desc">{{item.desc}}</p>
          <button class="item-button">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  data () {
    return {
      recommendList: [{
        id: '0001',
        imgUrl: 'http://img1.qunarzz.com/sight/p0/1810/4c/4c3e7f52ffd973b0a3.water.jpg_200x200_65b5a07f.jpg',
        title: '世界之窗',
        desc: '一个下午让你走遍全世界~'
      }]
    }
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/mixins.styl'
  .title
    line-height: .8rem
    background #eee
    text-indent .2rem
    margin-top: .2rem
  .item
    display flex
    height:1.9rem
    overflow hidden
    .item-img
      width 1.7rem
      height 1.7rem
      padding .1rem
    .item-info
      flex 1
      padding .1rem
      min-width 0
      .item-title
        line-height: .54rem
        font-size: .32rem
        ellipse()
      .item-desc
        line-height: .4rem
        color #ccc
        ellipse()
      .item-button
        margin-top: .16rem
        background #ff9300
        border-radius .06rem
        padding 0 .2rem
        line-height: .44rem
        color #fff
</style>
