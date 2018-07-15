<template>
	<div>
		<div class='recommend-title'>热门推荐</div>
		<ul>
			<li class='item border-bottom' v-for='item in list ' :key='item.id'>
				<div class="item-img-wrapper">
					<img :src="item.imgUrl" alt="" class='item-img'>
				</div>
				<div class='item-info'>
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class='item-button'>查看详情</button>
				</div>
			</li>
		</ul>
		<div class="all">查看所有产品</div>
	</div>
</template>

<script>
	export default{
		name:'HomeRecommend',
		data:function(){
			return {

			}
		},
		props:{
			list:Array
		}
	}
</script>

<style lang='stylus' scoped>
@import '~styles/mix.stylus'
	.recommend-title
		margin-top .4rem
		line-height .8rem
		background-color #eee
		text-indent .2rem
	.item
		display flex
		overflow hidden
		height 1.9rem
		.item-img
			width 1.7rem
			height 1.7rem
			padding .1rem
		.item-info
			flex 1
			padding .1rem
			min-width 0
			.item-title
				line-height .54rem
				font-size .32rem
				ellipsis()
			.item-desc
				line-height .4rem
				color #ccc
				ellipsis()
			.item-button
				padding 0 .2rem
				background-color deepskyblue
				border-radius .2rem
				color #fff
				margin-top .2rem
	.all
		line-height .8rem
		text-align:center
		width:100%
		color:#00afc7
</style>