<template>
	<div>
		<CityHeader></CityHeader>
		<CitySearch :cities="cities"></CitySearch>
		<CityList :cities="cities" :hotCities="hotCities" :letter="letter"></CityList>
		<Alphabet :cities="cities" @letterSupply="handelLetter"></Alphabet>
	</div>
</template>

<script>
	import axios from 'axios'
	import CityHeader from './components/city-header.vue'
	import CitySearch from './components/city-search.vue'
	import CityList from './components/city-list.vue'
	import Alphabet from './components/Alphabet.vue'
	export default{
		name:'City',
		components:{
			CityHeader:CityHeader,
			CitySearch:CitySearch,
			CityList:CityList,
			Alphabet:Alphabet
		},
		mounted (){
			this.getCityList()
		},
		data(){
			return {
				cities:{},
				hotCities:[],
				letter:''
			}
		},
		methods:{
			getCityList:function(){
				axios.get('api/city.json').then(this.getCityInfoSuccess)
			},
			getCityInfoSuccess:function(res){
				res=res.data
				if(res.ret && res.data){
					const data=res.data
					this.cities=data.cities
					this.hotCities=data.hotCities
				}
			},
			handelLetter (letter){
				this.letter=letter
			}
		}
	}
</script>

<style lang='stylus' scoped>
	
</style>