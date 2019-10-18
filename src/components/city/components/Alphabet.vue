<template>
  <ul class="list">
    <li class="item" v-for="item of letters"
        :key="item"
        :ref="item"
        @click="handleLetterClick"
        @touchstart="handleLetterStart"
        @touchmove="handleLetterMove"
        @touchend="handleLetterEnd"
    >
      {{item}}
    </li>
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
      touchStatus: '',
      startY: 0,
      timer: null
    }
  },
  computed: {
    letters () {
      return Object.keys(this.cities)
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop;
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerHTML.trim())
    },
    handleLetterStart (e) {
      console.log('触发')
      this.touchStatus = true
    },
    handleLetterMove (e) {
      if (this.touchStatus) {
        if (this.timer)
        {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          var touchY = e.touches[0].clientY - 79
          var index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleLetterEnd (e) {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  @import "~@/assets/styles/varibles.styl"
  .list
    position: absolute;
    top: 1.58rem;
    right: 0;
    bottom: 0;
    width: .4rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    .item
      text-align: center;
      line-height: .4rem;
      color: $bgColor;
</style>
