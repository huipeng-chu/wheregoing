<template>
  <div class="header">
    <div class="header-left"><div class="iconfont back-icon">&#xe624;</div></div>
    <div class="header-input"><span class="iconfont">&#xe632;</span>输入城市/游玩/主题</div>
    <router-link to="/city">
      <div class="header-right">{{this.city}}<span class="iconfont arrow-icon">&#xe64a;</span></div>
    </router-link>
  </div>
</template>

<script>
import {mapState} from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  /* font-size 86; 根是50px suoyi zhijieceliang / 100 */
  // @import '../../../assets/styles/varibles.styl'
  @import '~@/assets/styles/varibles.styl'
  .header
    display: flex;
    line-height: $headerHeight;
    background: #00bdc4;
    color: #fff;
    .header-left
      width: 0.64rem;
      float: left;
      .back-icon
        text-align: center;
        font-size: 0.3rem;
    .header-right
        min-width: 1.04rem;
        padding: 0 .1rem;
        float: right;
        text-align: center;
        color: #fff;
        .arrow-icon
          font-size: .24rem;
    .header-input
      flex: 1;
      height: .64rem;
      line-height: .64rem;
      margin-left: .2rem;
      margin-top: 0.12rem;
      background: #fff;
      color: #ccc;
      padding-left: .2rem;
</style>
