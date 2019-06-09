<template>
	<view>
		<view>
			<button type="primary" @click="fn">同步</button>
		</view>
		<view class="ct">同步了{{arr.length}}次</view>
		<view>
			<view v-for="(obj,index) in arr" class="list1" :key="index">{{obj}}</view>
		</view>
	</view>
</template>

<script>
	export default {
	    data() {
	        return {
	           arr:[],
	        }
	    },
		mounted(){
			uni.getStorage({
				key:'synchro',
				success:(res)=>{
					this.arr=res.data;
				}
				
			})
		},
	    methods: {
			fn(){
				var date =new Date();
				var ctime=date.getHours()+":"+date.getMinutes();
				this.arr.push("同步时间"+ctime);
				uni.setStorage({
					key:'synchro',
					data:this.arr
				})
				uni.getStorage({
					key: 'baseUser',
					success:(res)=> {
					var	compid=res.data.compid;
						uni.request({
							url: this.url+"produceReport/initCurrentDay?compid="+compid, 
							data: {
								
							},
							header: {
								'custom-header': 'hello' //自定义请求头信息
							},
							success: (res) => {
								uni.showToast({
									title:"采集成功"
								})
							}
						});
					}
				});
			}
	    },
		
	}
</script>

<style>
	@import url("../../static/css/person.css");
</style>
