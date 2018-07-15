<template>
	<div class="list" ref="wrapper">
		<div>
			<div class="area">
				<div class="area-title border-topbottom">当前城市</div>
				<div class="area-buttons">
					<div class="button-wrapper">
						<div class="button">{{this.$store.state.city}}</div>
					</div>
				</div>
			</div>
			<div class="area">
				<div class="area-title border-topbottom">热门城市</div>
				<div class="area-buttons">
					<div class="button-wrapper" v-for="item in hotCities" :key="item.id">
						<div class="button" @click="handelCityClick(item.name)">{{item.name}}</div>
					</div>
				</div>
			</div>
			<div class="area" v-for="(item,key) in cities" :key="key" :ref="key">
				<div class="area-title border-topbottom">{{key}}</div>
				<div class="area-itemlist" v-for="innerItem in item" :key="innerItem.id">
					<div class="item border-bottom" @click="handelCityClick(innerItem.name)">{{innerItem.name}}</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import BScroll from 'better-scroll'
	export default{
		name:'CityList',
		mounted:function(){
			this.scroll=new BScroll(this.$refs.wrapper)
		},
		props:{
			cities:Object,
			hotCities:Array,
			letter:String
		},
		watch:{
			letter:function(){
				this.scroll.scrollToElement(this.$refs[this.letter][0])
			}
		},
		methods:{
			handelCityClick (city){
				this.$store.dispatch('changeCity',city)
				this.$router.push('/')
			}
		}
	}
</script>

<style lang='stylus' scoped>
@import '~styles/variables.stylus'
.border-bottom
	&:before
		border-color:#ccc
.border-topbottom
	&:before
		border-color:#777
	&:after
		border-color:#777
.list
	position absolute
	top:1.79rem
	bottom 0
	left 0px
	right 0px
	overflow hidden
	.area
		.area-title
			line-height .44rem
			text-indent .2rem
			background-color #eee
			color #666
			font-size .26rem
		.area-buttons
			padding .1rem
			overflow hidden
			/*bfc原理*/
			padding .1rem .6rem .1rem .1rem
			.button-wrapper
				width 33.3%
				float left
				.button
					text-align center
					border .02rem solid #ccc
					margin .1rem
					padding .1rem 0
					border-radius .06rem
		.area-itemlist
			.item
				line-height .76rem
				padding-left .2rem
		
					
</style>