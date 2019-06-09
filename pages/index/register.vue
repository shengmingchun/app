<template>
	<view class="content">
		<input type="text" placeholder="请输入昵称" v-model="cname">
		<input type="text" placeholder="请输入用户名" v-model="username">
		<view>
			<input type="password" placeholder="请输入密码" v-model="password" v-if="fla">
			<input type="text" placeholder="请输入密码" v-model="password" v-if="!fla">
			<view class="l1">
				<uni-icon type="eye" size="30" @click="fn1"></uni-icon>
			</view>
			
		</view>
		 <radio-group @change="fn">
		  <radio value="男" checked="true"/>男
		  <radio value="女"/>女
		</radio-group>
		<input type="text" placeholder="请输入电话号码" v-model="telno">
		<input type="text" placeholder="请输入邮箱" v-model="email">
		<view>
			<picker @change="f1" :value="index" :range="arr" range-key="compname">
				<view class="uni-input">{{arr[index].compname}}</view>
            </picker>
		</view>
		<button type="primary" @click="register">注册</button>
	</view>
</template>

<script>
	import uniIcon from '@dcloudio/uni-ui/lib/uni-icon/uni-icon.vue'
	export default {
		components: {uniIcon},
		data() {
			return {
				fla:true,
				cname:'',
				username:'',
				password:'',
				flag:'password',
				sex:'',
				telno:'',
				email:'',
				arr:[{compname:""}],
				index:0,
			}
		},
		onLoad() {
				uni.request({
					url: this.url+'baseCompany/search', //仅为示例，并非真实接口地址。
					data: {
						
					},
					header: {
						'custom-header': 'hello' //自定义请求头信息
					},
					success: (res) => {
						this.arr=res.data;
					}
				});
				
			},
		methods: {
			f1(e){
				this.index = e.target.value
			},
			fn1(){
				this.fla=!this.fla;
			},
			fn(obj){
				this.sex=obj.detail.value;
			},
			register(){
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
					url: this.url+'baseUser/insert', //仅为示例，并非真实接口地址。
					data: {
						cname:this.cname,
						username:this.username,
						password:this.password,
						sex:this.sex,
						telno:this.telno,
						email:this.email,
						compid:this.arr[index].compid,
					},
					header: {
						'custom-header': 'hello' //自定义请求头信息
					},
					success: (res) => {
							uni.showToast({
								title: '注册成功',
								duration: 2000
							});
					},
					fail: (res) => {						
					},
					complete: (res) => {
					}
				});
			}
		}
	}
</script>

<style>
@import url("../../static/css/login.css");
</style>
