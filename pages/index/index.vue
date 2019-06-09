<template>
    <view>
		<wuc-tab :tab-list="items" :tabCur.sync="current" @change="onClickItem" :textFlex="true"></wuc-tab>
        <view class="content">
            <view v-show="current === 0">	
               <energy></energy>
            </view>
            <view v-show="current === 1">
                <run></run>
            </view>
            <view v-show="current === 2">
                选项卡3的内容
            </view>
        </view>
    </view>
</template>

<script>
import WucTab from '@/components/wuc-tab/wuc-tab.vue';
import energy from './energy.vue'
import run from "./run.vue"
export default {
    components: {WucTab,energy,run},
    data() {
        return {
            items: [{name:'总览'},{name:'运营'},{name:'局站'}],
            current: 0,
			time:'',
        }
    },
    methods: {
        onClickItem(index) {
            if (this.current !== index) {
                this.current = index;
            }
        },
    },
}
</script>

<style>
@import url("../../static/css/login.css");
</style>
