<template>
	<view class='body'>
		<button value='人机对战' @click="AI">人机对战</button>
		<button value='人人对战' @click="p2p">人人对战</button>		
		<!-- <button value='模拟对战'>模拟对战</button> -->
	</view>



</template>

<script>
	export default{
		data(){
			return {}
		},
		methods:{
			p2p(){
					uni.navigateTo({
						url: '../../pages/index/index?sel=p2p',
						success: res => {},
						fail: () => {},
						complete: () => {}
					});
			},
			AI(){
				uni.navigateTo({
					url: '../../pages/AIPage/AiPage?sel=AI',
					success: res => {
						console.log('进入人工智能界面');
					},
					fail: () => {},
					complete: () => {}
				});
			}
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
		margin: 30% 10%;
		background-size:100% 100%;
		background-repeat: no-repeat;
		background-image: url('../../static/img/stype_1/btn.png');
		
		
	}
</style>
