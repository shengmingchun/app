<template>
	<view>
		<view class="list">昵称:{{cname}}</view>
		<view class="list">用户名:{{username}}</view>
		<view class="list">电话号码:{{telno}}</view>
		<view class="list">邮箱地址:{{email}}</view>
		<view class="list">性别:{{sex}}</view>
		<view class="list">所属公司:{{compname}}</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
			 cname:"",
			 username:"",
			 telno:'',
			 email:'',
			 sex:'',
			 compname:''
			}
		},
		methods: {
		  
		},
		mounted() {
			var compid;
			uni.getStorage({
				key: 'baseUser',
				success:(res)=> {
					
					compid=res.data.compid;
					this.cname=res.data.cname;
					this.username=res.data.username;
					this.telno=res.data.telno;
					this.email=res.data.email;
					this.sex=res.data.sex;
					uni.request({
						url: this.url+"baseUser/search?compid="+compid, 
						data: {
							
						},
						header: {
							'custom-header': 'hello' //自定义请求头信息
						},
						success: (res) => {
							this.compname=res.data[0].baseCompany.compname;
						}
					});
				}
			});
		}
	}
</script>

<style>
@import url("../../static/css/person.css");
</style>
