<template>
	<div>
        <div class="title">热销推荐</div>
        <ul>
             <li class="item border-bottom" v-for="item of list" :key="item.id">
				<router-link :to="'/detail/'+item.id"  >
                <img class="item-img" :src="item.imgUrl" alt="">
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="desc">{{item.desc}}</p>
                    <button class="item-button">查看详情</button>
                </div>
               </router-link>
	        </li>
        </ul>
	</div>
</template>

<script>
	export default {
		name:'HomeRecommend',
        props:{
			list:Array
		}
	}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixins.styl'
.title
  margin-top: .2rem
  line-height: .8rem
  background: #eee
  text-indent: .2rem
.item
  position: relative
  overflow: hidden
  display: flex
  height: 1.9rem
  .item-img
    position: absolute
    width: 1.7rem
    height: 1.7rem
    padding:.1rem
  .item-info
    position: absolute
    flex: 1
    padding:.1rem
    margin-left: 1.8rem
    min-width: 0
    color: #333
    .item-title
      line-height: .54rem
      font-size: .32rem
      ellipsis()
    .item-desc
      line-height: .4rem
      color: #ccc
      ellipsis()
    .item-button
      margin-top: .24rem
      background: #ff9300
      padding: 0 .1rem
      border-radius: .06rem
      color: #fff
</style>