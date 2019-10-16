<template>
  <div class="swiper">
    <swiper :options="swiperOption" v-if="swiperList.length>1">
      <!-- slides -->
       <swiper-slide v-for="item of swiperList" :key="item.id">
          <img class="swiper-img" :src="item.imgUrl" alt="">
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true,
        autoplay: 3000
      },
      swiperList: [
        {
          id: '0001',
          imgUrl: 'https://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/201910/5ebde45f144a50e6427de9e74dad50d4.jpg_750x200_179eb37f.jpg'
        },
        {
          id: '0002',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1809/b1/5fb695dd812fdc02.jpg_750x200_6f896d28.jpg'
        },
        {
          id: '0003',
          imgUrl: 'https://imgs.qunarzz.com/piao/fusion/1803/98/0a2e0bd8eb0c0802.png_750x200_0a34d4a8.png'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  .swiper >>> .swiper-pagination-bullet-active
    background: #fff;
  .swiper
    overflow: hidden;
    width: 100%;
    height: 0;
    padding-bottom: 31.25%;
    .swiper-img
      width: 100%;
</style>
