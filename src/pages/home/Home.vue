<template>
  <div>
    <home-header :city="city"></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconList"></home-icons>
	<home-recommend :list="recommendList"></home-recommend>
	<home-weekend :list="weekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header.vue'
import HomeSwiper from './components/Swiper.vue'
import HomeIcons from './components/Icons.vue'
import HomeRecommend from './components/Recommend.vue'
import HomeWeekend from './components/Weekend.vue'
import {mapState} from 'vuex'
import axios from 'axios'
export default {
  name: 'Home',
  components:{HomeHeader,HomeSwiper,HomeIcons,HomeRecommend,HomeWeekend},
  data(){
	return {
		lastCity:'',
		swiperList:[],
		iconList:[],
		recommendList:[],
		weekendList:[]
	}
  },
  computed:{
    ...mapState(['city'])
// 	city: {
//      get() {
//        return this.$store.state.city;
//      },

//      set(val) {
//        // this.$store.state.city = val;
//      }
//    }
  },
  methods:{
	getHomeInfo(){
		axios.get('/api/index.json?city=' + this.city)
		  .then(this.getHomeInfoSucc)
	},
	getHomeInfoSucc(res){
		res=res.data
		console.log(res)
		if(res.ret && res.data){
			const data=res.data
			this.city=data.city
			this.swiperList=data.swiperList
			this.iconList=data.iconList
			this.recommendList=data.recommendList
			this.weekendList=data.weekendList
		}
	}
  },
  mounted(){
	this.lastCity=this.city
	this.getHomeInfo()
  },
  activated(){
	if(this.lastCity !== this.city){
		this.lastCity=this.city
        this.getHomeInfo()
	}
  } 
}
</script>

<style>

</style>
