<template>
	<div class="container" @click="handleGallaryClick">
		<div class="wrapper">
            <swiper :options="swiperOptions">
                <swiper-slide v-for="(item,index) of imgs" :key="index">
                    <img class="gallary-img" :src="item" alt="" />
                </swiper-slide>
				<div class="swiper-pagination" slot="pagination"></div>
            </swiper>
		</div>
	</div>
</template>

<script>
	export default {
		name:'CommonGallary',
		props:{
            imgs:{
				type:[Array,String],
				default(){
					return []
				}
			}
		},
		data(){
			return{
				swiperOptions:{
					autoplay:{
						delay:3000,
						disableOnInteraction:false
					},
                    pagination: {
                        el: '.swiper-pagination',
                        type:'fraction'
					},
					observerParents:true,
                    observer:true,
					loop:true,  
				}
			}
		},
		
		methods:{
			handleGallaryClick(){
				console.log('触发了Banner')
				this.$emit('close')
			}
		}
	}
</script>

<style lang="stylus" scoped>
    .container >>> .swiper-container
        overflow inherit
    .container
        display flex
        flex-direction column
        justify-content center
        z-index 99
        position fixed
        left 0
        right 0
        top 0
        bottom 0
        background #000
        .wrapper 
            height 0
            width 100%
            padding-bottom 100%  
            .gallary-img
                width 100%
                height 40vh
        .swiper-pagination
            color:#fff
            bottom -1rem
</style>