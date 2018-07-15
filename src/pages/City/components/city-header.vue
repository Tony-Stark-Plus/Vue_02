<template>
	<div>
		<div class='header'>
		城市选择
			<router-link to='/'>
				<div class="city-header-left">
					<p class='iconfont back-icon'>&#xe600;</p>
				</div>
			</router-link>
		</div>
		
	</div>
</template>

<script>

	export default{
		name:'CityHeader'
	}
</script>

<style lang='stylus' scoped>
@import '~styles/variables.stylus'
	.header
		position relative
		height:.86rem
		line-height:.86rem
		overflow hidden
		background-color $bgColor
		text-align:center
		color:#fff
		.city-header-left
			position absolute
			top 0
			left .1rem
			.back-icon
				font-size .42rem
				color #fff
</style>