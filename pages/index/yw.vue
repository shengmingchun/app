<template>
    <view>
		<wuc-tab :tab-list="items" :tabCur.sync="current" @change="onClickItem" :textFlex="true"></wuc-tab>
        <view class="content">
            <view v-show="current === 0">	
				<synchro></synchro>
            </view>
            <view v-show="current === 1">
               <phones></phones>
            </view>
            <view v-show="current === 2">
                选项卡3的内容
            </view>
        </view>
    </view>
</template>

<script>
import WucTab from '@/components/wuc-tab/wuc-tab.vue';
import synchro from '../yw/synchro.vue'
import phones from "../index/phones.vue"
export default {
    components: {WucTab,synchro,phones},
    data() {
        return {
            items: [{name:'数据采集'},{name:'通讯录'},{name:'故障记录'}],
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
