<template>
  <div>
    <div class="content">
        <div class="shop">            
            <div class="top">
                <div class="my-container">
                    <div class="img">
                        <img class="img-add" :src="imgUrl">
                    </div>
                </div>
            </div>

            <div class="bottom">
                <div class="my-container">
                    <div class="item">
                        <p class="p-title">商铺名称</p>
                        <p class="p-content">{{ name }}</p>
                    </div>
                    <div class="item">
                        <p class="p-title">经营类型</p>
                        <p class="p-content">{{ type }}</p>
                    </div>
                    <div class="item">
                        <p class="p-title">地理位置</p>
                        <p class="p-content">{{ position }}</p>
                    </div>
                    <div class="item">
                        <p class="p-title">联系方式</p>
                        <p class="p-content">{{ num }}</p>
                    </div>
                    <div class="item">
                        <p class="p-title">商铺介绍</p>
                        <p class="p-content">{{ desc }}</p>
                    </div>
                </div>
            </div>

        </div>
        <p class="edit">编辑</p>
    </div>
  </div>
</template>

<script>
import { formatTime } from '@/utils/index'
import card from '@/components/card'


export default {
  components: {
    card
  },

  data () {
    return {
      imgUrl: 'https://raw.githubusercontent.com/w112452258/w112452258.github.io/master/dingding/add2.png',
      name: '啊啊啊',
      type: '车品-美容',
      position: '湖南省株洲市天元区泰山路',
      num: '13545454545',
      desc: '啊啊啊'
    }
  },

  created () {
    let logs
    if (mpvuePlatform === 'my') {
      logs = mpvue.getStorageSync({key: 'logs'}).data || []
    } else {
      logs = mpvue.getStorageSync('logs') || []
    }
    this.logs = logs.map(log => formatTime(new Date(log)))
  }
}
</script>

<style scoped>
  .content {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: #f2f2ff;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding: 0;
    overflow: auto;
    padding-bottom: 120rpx;
  }

  .shop {
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
  }
  
  .my-container {
    width: 90%;
    /* background-color: red; */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 0 20rpx;
  }

  .top {
      width: 100%;
      height: 300rpx;
      background-color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-bottom: 10rpx;
  }

  .img {
      width: 200rpx;
      height: 200rpx;
      border: 1px solid #cccccc;
      display: flex;
      justify-content: center;
      align-items: center;
  }

  .img-add {
      width: 100rpx;
      height: 100rpx;
      /* border: 1px solid #000; */
  }

  .bottom {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #fff;
  }

  .item {
      height: 80rpx;
      width: 100%;
      padding: 0 5rpx;
      display: flex;
      justify-content: space-between;
      border-bottom: 1px solid #e2e2e2;
  }

  .p-title {
    font-size: 13px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .p-content {
    font-size: 13px;
    color: #999999;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .edit {
    width: 90%;
    height: 80rpx;
    border-radius: 40rpx;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    background-color: #3399ff;
    /* box-shadow: 0 0 5rpx #3399ff; */
    position: fixed;
    bottom: 20rpx;
  }

</style>
