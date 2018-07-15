 <template>
	<div>
		<HomeHeader></HomeHeader>
		<HomeSwiper :swiperList='swiperList'></HomeSwiper>
		<HomeIcons :iconList='iconList'></HomeIcons>
		<HomeRecommend :list='recommendList'></HomeRecommend>
		<Weekend :list='weekendList'></Weekend>
	</div>
</template>

<script>
import HomeHeader from './components/header.vue'
import HomeSwiper from './components/homeswiper.vue'
import HomeIcons from './components/homeicons.vue'
import HomeRecommend from './components/homerecommend.vue'
import Weekend from './components/weekend.vue'
import axios from 'axios'
/*引入组件*/

export default
	{
		name:'Home',
		components:{
			HomeHeader:HomeHeader,
			HomeSwiper:HomeSwiper,
			HomeIcons:HomeIcons,
			HomeRecommend:HomeRecommend,
			Weekend:Weekend
			/*注册局部组件*/
		},
		mounted: function (){
			 this.getHomeInfo()
		},
		methods:{
			getHomeInfo:function () {
				axios.get('/api/index.json').then(this.getHomeInfoSuccess)
			},
			getHomeInfoSuccess:function(res){
				var res=res.data
				if(res.ret && res.data){
					const data=res .data
					this.iconList=data.iconList
					this.swiperList=data.swiperList
					this.recommendList=data.recommendList
					this.weekendList=data.weekendList
				}
			}
		},
		data:function(){
			return {
				iconList:[ ],
				swiperList:[ ],
				recommendList:[],
				weekendList:[]
			}
		}

	}
</script>

<style>
	
</style>
