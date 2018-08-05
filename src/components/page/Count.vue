<template>
	<div>
		<h2>{{message}}</h2>
		<hr>
		<h3>{{$store.state.count}}---{{count}}</h3>
		<!-- 模块引用后 -->
		<!-- <h3>{{$store.state.a.count}}</h3> -->
		<p>
			<!-- 方法名，变量 -->
			<button @click="$store.commit('add',10)">+</button>
			<button @click="$store.commit('reduce')">-</button>
		</p>
		<p>
			<button @click="addAction">+</button>
			<button @click="reduceAction">-</button>
		</p>

	</div>
</template>

<script>
import store from '@/vuex/store';
import {mapState,mapMutations,mapGetters,mapActions} from 'vuex';
export default{
	data(){
		return{
			message:'Hello Vuex'
		}
	},
	computed:{
		...mapState(['count']),
		// count(){
		// 	return this.$store.getters.count;
		// }
		// ...mapGetters(['count'])
		// 引入模块后
		//count(){
		// 	return this.$store.a.count;
		// }

	},
	/*ES5
	computed:mapState({
		count:function(state){
			return state.count;
		}
	})*/
	/*ES6
	computed:mapState({
			count:state=>state.count
		}),
	*/
	methods:{
		...mapMutations(['add','reduce']),
		...mapActions(['addAction','reduceAction'])
	},
	store
}
</script>