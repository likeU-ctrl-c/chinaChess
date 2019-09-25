<template>
	<view class='body'>
		<button value='人机对战' @click="AI1">脑残人机对战</button>
		<button value='人机对战' @click="AI2">智障人机对战</button>
		<button value='人机对战' @click="AI3">入门人机对战</button>
		<button value='人机对战' @click="AI4">入门人机优化+剪枝对战</button>		
		<!-- <button value='模拟对战'>模拟对战</button> -->
	</view>



</template>

<script>
	export default{
		data(){
			return {
				id:'',
			}
		},
		methods:{
			AI2(){
				uni.navigateTo({
					url: '../../pages/index/index?id=AI&sel=AI2',
					success: res => {
						console.log('进入入门人工智能界面');
					},
					fail: () => {},
					complete: () => {}
				});
			},
			AI1(){
				uni.navigateTo({
					url: '../../pages/index/index?id=AI&sel=AI1',
					success: res => {
						console.log('进入脑残人工智能界面');
					},
					fail: () => {},
					complete: () => {}
				});
			},
		AI3(){
				uni.navigateTo({
					url: '../../pages/index/index?id=AI&sel=AI3',
					success: res => {
						console.log('进入入门人工智能界面');
					},
					fail: () => {},
					complete: () => {}
				});
			},
			AI4(){
					uni.navigateTo({
						url: '../../pages/index/index?id=AI&sel=AI4',
						success: res => {
							console.log('进入入门剪枝人工智能界面');
						},
						fail: () => {},
						complete: () => {}
					});
				},
			
		},
		onLoad(e) {
			console.log(e);
			this.id=e.sel;
		}
	}
	
</script>

<style>
	.body{
		margin: 0;
		width: 100%;
		height: 100%;
		background-repeat: no-repeat;
		background-image: url('../../static/img/stype_1/bg.jpg');
		background: auto;
		position: fixed;
	}
	button{
		margin: 25% 10%;
		background-size:100% 100%;
		background-repeat: no-repeat;
		background-image: url('../../static/img/stype_1/btn.png');
		
		
	}
</style>
