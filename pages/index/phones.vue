<template>
	<view>
		<phone-directory :phones="phones" @paramClick="paramClick"></phone-directory>
	</view>
</template>

<script>
	import phoneDirectory from '@/components/phone-directory/phone-directory.vue'
	export default {
		name:"phones",
		components:{
			phoneDirectory
		},
		data() {
			return {
				//示例数据
				phones:{}
			}
		},
		methods : {
			paramClick (e) {
				console.log(e)
			}
		},
		mounted(){
			uni.request({
				url: this.url+"baseUser/applist", 
				data: {
					
				},
				header: {
					'custom-header': 'hello' //自定义请求头信息
				},
				success: (res) => {
					console.log(res.data);
					this.phones=res.data;
				}
			});
		}
	}
</script>

<style>

</style>
