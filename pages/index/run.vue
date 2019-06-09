<template>
	<view>
		<view class="main">
			<view class="top1">
				21天
			</view>
			<view class="body1">
				<text class="top2">~</text>
				<text class="top3">警告统计</text>
				<image src="../../static/yw1.png" class="top4"></image>
			</view>
			<view>
				<uni-list>
					<uni-list-item title="创立二楼IDC机房..." @click='fn()' show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"
					 show-badge="true" badge-text="04-30"></uni-list-item>
					<uni-list-item title="创立二楼IDC机房..." @click='fn1()' show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"
					 show-badge="true" badge-text="08-25"></uni-list-item>
					<uni-list-item title="创立二楼IDC机房..." @click='fn("流程fm3")' show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"
					 show-badge="true" badge-text="08-30"></uni-list-item>
					 <uni-list-item title="创立二楼IDC机房..." @click='fn("流程fm4")' show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"
					  show-badge="true" badge-text="09-11"></uni-list-item>
				</uni-list>
			</view>
		</view>
	</view>	
</template>

<script>
	import uniList from '@dcloudio/uni-ui/lib/uni-list/uni-list.vue'
	import uniListItem from '@dcloudio/uni-ui/lib/uni-list-item/uni-list-item.vue'
	import table01 from '../table/table01.vue'
export default {
	components: {uniList,uniListItem,table01},
	data() {
		return {
		  
		}
	},
	methods: {
	  fn(){
		  uni.navigateTo({
		  	url:"../charts/chart02"
		  })
	  },
	  fn1(){
	  		  uni.navigateTo({
	  		  	url:"../table/table01"
	  		  })
	  },
	},
	mounted() {
	
	}
}
</script>

<style>
	@import url("../../static/css/index.css");
