<template>
	<div>
		<div class="search">
			<input type="text" class='search-input' placeholder="请输入城市名称或拼音" v-model="keyword">
		</div>
		<div class="search-content" ref="sear" v-show="keyword">
			<ul>
				<li v-for="item in list" class="search-item border-bottom" :key="item.id"
				@click="handelCityClick(item.name)">{{item.name}}</li>
				<li class="search-item border-bottom" v-show="hasNoData">没有匹配数据</li>
			</ul>
		</div>
	</div>
</template>
s
<script>
	import BScroll from 'better-scroll'
	export default{
		name:'CitySearch',
		data (){
			return {
				keyword:'',
				list:[],
				timer:null
			}
		},
		mounted:function(){
			this.scroll=new BScroll(this.$refs.sear)
		},
		props: {
			cities:Object
		},
		watch: {
			keyword (){
				if(this.timer){
					clearTimeout(this.timer)
				}
				/* 当输入框无值时，查询列表会显示是最后一次查询结果 */
				if(!this.keyword){
					this.list=[]
					return
				}
				this.timer=setTimeout( () => {
					const result =[]
					for (let i in this.cities){
						this.cities[i].forEach( (val) =>{
							if(val.spell.indexOf(this.keyword) >-1 || val.name.indexOf(this.keyword) >-1){
								result.push(val)
							}
						})
					}
					this.list=result
				},100)
			}
		},
		computed:{
			hasNoData (){
				return !this.list.length
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
	.search
		height:.72rems
		background-color $bgColor
		padding:.1rem .1rem
		.search-input
			box-sizing border-box
			height:.62rem
			width:100%
			text-align center
			border-radius .1rem
			color:#666
			padding 0  .1rem
	.search-content
		position absolute
		top:1.8rem
		left 0
		right 0
		bottom 0
		background-color #eee
		z-index 1
		.search-item
			line-height:.62rem
			padding-left .2rem
			color #666
			background #fff
</style>