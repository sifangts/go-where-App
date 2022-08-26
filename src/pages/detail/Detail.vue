<template>
	<div >
		<detail-banner></detail-banner>
		<detail-header></detail-header>
		<div class="content"></div>
	</div>
</template>

<script>
    import DetailBanner from './componments/Banner.vue'
	import DetailHeader from './componments/Header.vue'
	export default {
		name:'Detail',
		components:{
			DetailBanner,
			DetailHeader
		}
	}
</script>

<style lang="stylus" scoped>
</style>