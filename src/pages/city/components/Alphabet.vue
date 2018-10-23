<template>
  <ul class="list">
    <li class="item"
        v-for="(item, key) of cities"
        :key="key"
        :ref="key"
        @click="letterClick"
        @touchstart="touchStart"
        @touchmove="touchMove"
        @touchend="touchEnd"
    >{{key}}</li>
  </ul>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  methods: {
    letterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    touchStart () {
      this.touchStatus = true
    },
    touchMove (e) {
      if (this.touchStatus === true) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const startY = this.startY
          const touchY = e.touches[0].clientY - 79
          const index = Math.floor((touchY - startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    touchEnd () {
      this.touchStatus = false
    }
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(i)
      }
      return letters
    }
  }
}
</script>

<style scoped lang="stylus">
  @import '~styles/varibles.styl'
  .list
    display flex
    flex-direction column
    justify-content center
    position: absolute
    top: 1.58rem
    right: 0
    bottom 0
    width .4rem
    .item
      line-height: .4rem
      text-align center
      color: $bgColor
</style>
