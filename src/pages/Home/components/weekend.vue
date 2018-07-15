<template>
	<div>
		<div class="weekend-title">周末去哪儿</div>
		<ul>
			<li class='item border-bottom' v-for='item in list' :key='item.id'>
				<div class='item-img-wrapper'>
				<img :src="item.imgUrl" alt="" class='item-img'>
				</div>
				<div class='item-title'>{{item.title}}</div>
				<div class="item-desc">{{item.desc}}</div>
			</li>
		</ul>
	</div>
</template>

<script>
	export default{
		name:'Weekend',
		props:{
			list:Array
		}
	}
</script>

<style lang='stylus' scoped>
@import '~styles/mix.stylus'
	.weekend-title
		line-height .8rem
		background-color #eee
		text-indent:.4rem
	.item-img-wrapper
		width 100%
		height:0
		padding-bottom 37.1%
		overflow  hidden
		.item-img
			width:100%
	.item-title
				line-height .54rem
				font-size .28rem
				ellipsis()
				text-indent:.1rem
			.item-desc
				line-height .4rem
				color #ccc
				ellipsis()
				font-size .22rem
				text-indent:.1rem
</style>
