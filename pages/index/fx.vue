<template>
	<view>
		<uni-list>
			<uni-list-item title="港口能耗对比" @click='fn(1)' show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"
			 show-badge="true" badge-text="04-30"></uni-list-item>
			<uni-list-item title="流程作业量对比" @click='fn(2)' show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"
			 show-badge="true" badge-text="08-25"></uni-list-item>
			<uni-list-item title="创立二楼IDC机房..." @click='fn(3)' show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"
			 show-badge="true" badge-text="08-30"></uni-list-item>
			 <uni-list-item title="创立二楼IDC机房..." @click='fn(4)' show-extra-icon="true" :extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"
			  show-badge="true" badge-text="09-11"></uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	import uniList from '@dcloudio/uni-ui/lib/uni-list/uni-list.vue'
	import uniListItem from '@dcloudio/uni-ui/lib/uni-list-item/uni-list-item.vue'
	export default {
		components: {uniList,uniListItem},
		data() {
			return {
			  
			}
		},
		methods: {
		  fn(index){
			  if(index==1){
					uni.navigateTo({
						url:"../charts/chart02"
					})
				}
			  if(index==2){
					
				}
			  if(index==3){
					
				}
				 
		  }
		},
		mounted() {
		
		}
	}
</script>

<style>
</style>
