<template>
  <div id="app">
	<keep-alive exclude="Detail"><!-- 使用exclude内容不再被缓存 -->
        <router-view/>
	</keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>

</style>
