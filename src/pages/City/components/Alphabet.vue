<template>
	<ul class="list">
		<li class="item" v-for="item in letters" :key="item" :ref="item"
		@click="handleLetterClick"
		@touchstart="handleTouchStart"
		@touchmove="handleTouchMove"
		@touchend="handleTouchEnd">
			{{item}}
		</li>
	</ul>
</template>

<script>
	export default{
		name:'Alphabet',
		props:{
			cities:Object
		},
		methods:{
			handleLetterClick:function(e){
				this.$emit('letterSupply',e.target.innerText)
			},
			handleTouchStart (){
				this.touchStatus= true
			},
			handleTouchMove (e){
				if(this.touchStatus){
					if(this.timer){
						clearTimeout(this.timer)
					}
					this.timer=setTimeout( () =>{
						const touchY =e.touches[0].clientY - 89
						const index =Math.floor((touchY-this.startY)/20)
						if(index >=0 && index <this.letters.length)
						{
						this.$emit('letterSupply',this.letters[index])
						}
					},10)	
				}
			},
			handleTouchEnd (){
				this.touchStatus= false
			}
		},
		computed:{
			letters (){
				const letters=[]
				for (var i in this.cities) {
					letters.push(i)
				}
				return letters
			}
		},
		data (){
			return {
				touchStatus: false,
				startY: 0,
				timer: null
			}
		},
		updated (){
			this.startY=this.$refs['A'][0].offsetTop
		}
	}
</script>

<style lang='stylus' scoped>
.list
	position absolute
	right 0
	top 1.79rem
	bottom 0
	display flex
	justify-content center
	width .4rem
	flex-direction:column
	.item
		color:red
		text-align center
		line-height .4rem
       					
</style>