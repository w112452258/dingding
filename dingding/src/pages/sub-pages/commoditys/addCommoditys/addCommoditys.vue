<template>
  <div>
    <div class="content">
      <div class="addCommoditys">
        <div class="my-container">
          <div class="item">
            <p class="p-title">商品名称</p>
            <p class="p-content">aaaaaa</p>
          </div>

          <div class="item">
            <p class="p-title">商品类型</p>
            <picker mode="multiSelector" @change="bindPickerChange" :value="index" :range="multiArray" @columnchange="bindMultiPickerColumnChange">
              <div class="picker">
                <p class="p-content">{{ multiArray[0][multiIndex[0]] }}，{{multiArray[1][multiIndex[1]]}}</p>
              </div>
            </picker>
          </div>

          <div class="item">
            <p class="p-title">单价</p>
            <p class="p-content">152.00</p>
          </div>

          <div class="item">
            <p class="p-title">是否参与活动</p>
            <p class="p-content">是</p>
          </div>

        </div>
      </div>
    </div>
  </div>





<!-- 
  <picker mode="multiSelector" @change="bindPickerChange" :value="index" :range="multiArray" @columnchange="bindMultiPickerColumnChange">
      <div class="picker">
        当前选择：{{ multiArray[0][multiIndex[0]] }}，{{multiArray[1][multiIndex[1]]}}
      </div>
    </picker> -->


</template>

<script>
import { formatTime } from "@/utils/index";
import card from "@/components/card";

export default {
  components: {
    card
  },

  data() {
    return {
      // value: '',
      index: 0,
      multiArray: [['A', 'B'], ['1', '2', '3', '4']],
      multiIndex: [0, 0]
    };
  },

  created() {
    let logs;
    if (mpvuePlatform === "my") {
      logs = mpvue.getStorageSync({ key: "logs" }).data || [];
    } else {
      logs = mpvue.getStorageSync("logs") || [];
    }
    this.logs = logs.map(log => formatTime(new Date(log)));
  },

  methods: {
    bindPickerChange (e) {
      console.log(e.mp.detail.value),
      this.multiIndex = e.mp.detail.value
    },

    bindMultiPickerColumnChange(e) {
      // console.log(e.mp.detail.column),
      // console.log(this.multiIndex[0]),
      // console.log(e.mp.detail.value)
      if( e.mp.detail.column === 0 ) {
        if( e.mp.detail.value === 1) {
          this.multiArray = [['A', 'B'], ['5', '6', '7', '8']]
        } else {
          this.multiArray = [['A', 'B'], ['1', '2', '3', '4']]
        }
      }
    }
  }
};
</script>

<style scoped>
.content {
    /* position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0; */
    background-color: #f2f2ff;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding: 0;
    overflow-y: auto;
    padding-bottom: 120rpx;
  }
  
  .addCommoditys {
    width: 100%;
    display: flex;
    justify-content: center;
    background-color: #fff;
  }

  .my-container {
    width: 90%;
  }

  .item {
    width: 100%;
    height: 80rpx;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid #cccccc;
    /* padding: 30rpx 0; */
  }

  /* .p-title {

  } */

  .p-content {
    color: #999999;
  }

</style>
