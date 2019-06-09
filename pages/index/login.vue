<template>
	<view class="content">
		<input type="text" placeholder="请输入用户名" v-model="username">
		<view>
			<input type="password" placeholder="请输入密码" v-model="password" v-if="fla">
			<input type="text" placeholder="请输入密码" v-model="password" v-if="!fla">
			<view class="l1">
				<uni-icon type="eye" size="30" @click="fn"></uni-icon>
			</view>
			
		</view>
		<button type="primary" @click="login">登录</button>
		<button type="primary" @click="register">注册</button>
	</view>
</template>

<script>
	import uniIcon from '@dcloudio/uni-ui/lib/uni-icon/uni-icon.vue'
	export default {
		components: {uniIcon},
		onNavigationBarButtonTap() {
			uni.navigateTo({
				url:'register'
			})
		},
		data() {
			return {
				username:'lhx',
				password:'123456',
				fla:true,
			}
		},
		onLoad() {

		},
		methods: {
			register(){
				uni.navigateTo({
					url: 'register'
				});
			},
			login(){
				if(this.username.length<=0){
					uni.showToast({
						title: '请输入用户名',
						duration: 2000,
						
					});
					return;
				}
				if(this.password.length<=0){
					uni.showToast({
						title: '请输入密码',
						duration: 2000,		
					});
					return ;
				}
				uni.request({
					url: this.url+'baseUser/login', //仅为示例，并非真实接口地址。
					data: {
						username: this.username,
						password:this.password
					},
					header: {
						'custom-header': 'hello' //自定义请求头信息
					},
					success: (res) => {
						if((this.username!=res.data.username && this.password!=res.data.password ) ){
							uni.showToast({
								title: '登录失败',
								duration: 2000
							});
						}else{
							uni.switchTab({
								url: 'index'
							})
							// uni.navigateTo({
							// 	url: 'index'
							// });
							uni.setStorage({
								key: 'baseUser',
								data: res.data,	
							});
						}
						
					},
					fail: (res) => {						
					},
					complete: (res) => {
					}
				});
			},
			fn(){
				this.fla=!this.fla;
			}
		}
	}
</script>

<style>
@import url("../../static/css/login.css");
</style>
