<template>
  <div>
    <div class="content">
      <div class="addCommoditys">
        <div class="my-container">
          <div class="item" @click="showModifyTitle">
            <p class="p-title">商品名称</p>
            <p class="p-content">{{ name }}</p>
          </div>

          <div class="item">
            <p class="p-title">商品类型</p>
            <picker mode="multiSelector" @change="bindPickerChangeType" :value="index" :range="multiArray" @columnchange="bindMultiPickerColumnChange">
              <div class="picker">
                <p class="p-content">{{ multiArray[0][multiIndex[0]] }}，{{multiArray[1][multiIndex[1]]}}</p>
              </div>
            </picker>
          </div>

          <div class="item">
            <p class="p-title">单价</p>
            <!-- <p class="p-content">152.00</p> -->
            <input type="digit" class="input-num" v-model.lazy="num"/>
          </div>

          <div class="item">
            <p class="p-title">是否参与活动</p>
            <picker @change="bindPickerChange" :value="index" :range="array">
              <div class="picker">
                <p class="p-content">{{ array[index] }}</p>
              </div>
            </picker>
          </div>

          <div class="item">
            <p class="p-title">优惠方式</p>
            <picker @change="bindPickerChange1" :value="index1" :range="array1">
              <div class="picker">
                <p class="p-content">{{ array1[index1] }}</p>
              </div>
            </picker>
          </div>

          <div class="item" @click="showModifyDesc">
            <p class="p-title">商品描述</p>
            <p class="p-content">{{ desc }}</p>
          </div>

          <p class="add-commodity" @click="commodity">添加商品</p>

        </div>
      </div>

      <div class="modify-title" v-if="showModify">
        <div class="my-container">
          <form @submit="bindFormSubmit">
            <div class="submit">
              <p class="p-cancel" @click="showModify=false">取消</p>
              <button class="btn-submit" form-type="submit">确定</button>
            </div>
            <textarea class="ta-title" name="textarea" focus="true" :show-confirm-bar="false"></textarea>
          </form>
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
      name: '啊啊啊啊啊',
      desc: '哈哈哈哈',
      num: '152.00',
      // value: '',
      multiArray: [['A', 'B'], ['1', '2', '3', '4']],
      multiIndex: [0, 0],
      array: ['满100减10', '满150减20', '满300减50'],
      array1: ['是', '否'],
      index: 0,
      index1: 0,
      showModify: false,
      ta: ''
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
    bindPickerChangeType (e) {
      console.log(e.mp.detail.value),
      this.multiIndex = e.mp.detail.value
    },

    bindPickerChange (e) {
      console.log(e.mp.detail.value),
      this.index = e.mp.detail.value
    },

    bindPickerChange1 (e) {
      console.log(e.mp.detail.value),
      this.index1 = e.mp.detail.value
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
    },

    bindFormSubmit(e) {
      if ( this.ta === 'title' ){
        console.log(e.mp.detail.value.textarea),
        this.name = e.mp.detail.value.textarea,
        this.showModify = false,
        console.log(this.num)
      } else if ( this.ta === 'desc' ){
        console.log(e.mp.detail.value.textarea),
        this.desc = e.mp.detail.value.textarea,
        this.showModify = false
      }
    },

    showModifyTitle() {
      this.ta = 'title',
      this.showModify = true
    },

    showModifyDesc() {
      this.ta = 'desc',
      this.showModify = true
    },

    commodity() {
        wx.navigateBack({
        delta: 1
      })
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
    /* padding-bottom: 120rpx; */
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
    max-width: 400rpx;
    color: #999999;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    /* display: flex;
    justify-content: flex-end; */
  }

  .input-num {
    width: 200rpx;
    color: #999999;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    padding: 0;
    text-align: right;
  }

  .modify-title {
    width: 100%;
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    border-top: 1px solid #cccccc;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }

  .submit {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    /* background-color: aqua; */
  }

  .p-cancel {
    font-size: 14px;
    padding: 10rpx 5rpx;
    color: #3399ff;
  }

  .btn-submit {
    font-size: 14px;
    color: #3399ff;
    border: none;
    background-color: #fff;
    margin: 0;
  }

  .btn-submit::after{
    border: none;
  }

  .ta-title {
    width: 100%;
    border-top: 1px solid #cccccc;
  }

  .add-commodity {
    width: 100%;
    height: 80rpx;
    border-radius: 40rpx;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    background-color: #3399ff;
    /* box-shadow: 0 0 5rpx #3399ff; */
    /* position: fixed;
    bottom: 20rpx; */
    margin: 50rpx 0;
  }

</style>
