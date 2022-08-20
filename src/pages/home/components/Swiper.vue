<template>
  <div class="wrapper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl" alt="" />
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: "HomeSwiper",
  data(){
    return {
      swiperOption: {
        pagination: {
            el:".swiper-pagination",//分页器的类名
            clickable:true//设置分页小圆点可手动点击
        },
        loop:true,
        },
        swiperList:[{
            id:'0001',
            imgUrl:"https://source.qunarzz.com/site/images/wns/20220805_qunar_dujia_homepage_a750x192_v4.jpg"
        },{
            id:'0002',
            imgUrl:"https://source.qunarzz.com/site/images/wns/20220727_qunar_dujia_homepage_a750x192_v8.jpg"
        }]
      }
  },
}
</script>

<style lang="stylus" scoped>
.wrapper >>>.swiper-pagination-bullet-active {
  background: #fff !important;
}

.wrapper {
  overflow: hidden;
  width: 100%;
  height: 0;
  padding-bottom: 25.6%;
  background: #eee;

  .swiper-img {
    width: 100%;
  }
}
</style>