<template>
	<view>
		<view class="top">
			<view class="time">
				 <text>{{time}}</text>
			</view>
			<view class="second">
				<view class="second-1">4560.10</view> 
				<view class="second-2">总kw/h</view>
			</view>
			<view class="third">
				<view class="third-2">
					<image src="../../static/water.png" mode=""></image>
					<view class="third-1">4560.10</view> 
					<view class="third-1">总kw/h</view>
				</view>
				<view  class="third-2">
					<image src="../../static/ele.png" mode=""></image>
					<view class="third-1">4560.10</view> 
					<view class="third-1">总kw/h</view>
				</view>
				<view  class="third-2">
					<image src="../../static/oil.png" mode=""></image>
					<view class="third-1">4560.10</view> 
					<view class="third-1">总kw/h</view>
				</view>
			</view>
		</view>
		<view class="body">
			<view class="but">
				<button class="but1" @click="f1" :style="{background:color1}">日</button>
				<button class="but2" @click="f2" :style="{background:color2}">月</button>
			</view>
			<view class="">
				<chart01></chart01>
			</view>
		</view>
	</view>
</template>

<script>
	import chart01 from"../charts/chart01.vue"
	export default {
		components: {chart01},
	    data() {
	        return {
	           time:'', 
			   color1:'blue',
			   color2:'#ccc'
	        }
	    },
	    methods: {
	       f1(){ 
			    var date=new Date();
			    this.time=(date.getUTCMonth()+1)+"月"+date.getUTCDate()+"日";
			    this.color2='#ccc';
				this.color1='blue';
		   },
		   f2(){	   
				var date=new Date();
			    this.time=(date.getUTCMonth()+1)+"月";	
				this.color1='#ccc';
				this.color2='blue';
		   }
	    },
		mounted() {
			var date=new Date();
			this.time=(date.getUTCMonth()+1)+"月"+date.getUTCDate()+"日";
		}
	}
</script>


<style>
@import url("../../static/css/index.css");
</style>
