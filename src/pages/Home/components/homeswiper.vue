<template>
<div class='wrapper'>
<swiper :options="swiperOption" v-if='showSwiper'>
    <!-- slides -->
    <swiper-slide v-for='item in swiperList' :key='item.id'>
    <img  class='swiper-img' :src="item.imgUrl" alt="">
    </swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
</swiper>
</div>
</template>

<script>
	export default{
		name:'HomeSwiper',
		data:function(){
			return{
				swiperOption:{ 
					pagination:'.swiper-pagination', 
					loop:'true',
					
				}
			}
		},
		props:{
			swiperList:Array
		},
		computed:{
			showSwiper(){
				return this.swiperList.length
			}
		}
	}
</script>

<style lang="stylus" scoped>
.wrapper >>> .swiper-pagination-bullet-active
	background-color red
.wrapper
	overflow hidden
	width:100%
	height:0
	padding-bottom:28.6%
	.swiper-img
		width:100%
</style>
