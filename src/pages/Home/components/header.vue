 <template>
	<div class="header">
		<div class="header-left">
			<p class='iconfont back-icon'>&#xe600;</p>
		</div>

		<div class="header-input">
			<span class="iconfont">&#xe65a;</span>
			输入城市/景点/游玩主题
		</div>

		<router-link to='/city'>	
		<div class="header-right">{{this.$store.state.city}}
			<span class="iconfont">&#xe64a;</span>
		</div>
		</router-link>
	</div>	
</template>

<script>
export default 
{
	name:'HomeHeader'
}
</script>

<style lang='stylus' scoped>
@import '~styles/variables.stylus'
	.header
		display:flex
		background-color:$bgColor
		line-height:0.86rem
		color #fff
		.header-left
			width:0.64rem
			float:left
			.back-icon
				text-align:center
				font-size .4rem
				width:100%
				height:100%
		.header-input
			flex:1
			background-color:#fff
			border-radius:0.1rem
			margin-top :0.12rem
			margin-bottom :0.12rem 
			line-height:0.64rem
			margin-left:.2rem
			color black
			padding-left .2rem
		.header-right
			width:1.24rem
			float:right
			text-align:center
			color:#fff
</style>
