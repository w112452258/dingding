<template>
  <div>
    <div class="content">
        <div class="top">
            <img class="img-code" :src="code">
            <p class="p-again">重新生成二维码</p>
        </div>
        <div class="bottom">
            <p class="p-share">分享至微信</p>
            <p class="p-share">分享至朋友圈</p>
        </div>
    </div>
  </div>
</template>

<script>
import { formatTime } from '@/utils/index'
import card from '@/components/card'
import { 
    like_icon
  } from './../../assets/icon'


export default {
  components: {
    card
  },

  data () {
    return {
      code: ''
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
  }

  .top {
      padding: 100rpx;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
  }

  .img-code {
      width: 400rpx;
      height: 400rpx;
      background-color: aqua;
  }

  .p-again {
      color: #3399ff;
      margin-top: 50rpx;
  }

  .bottom {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
  }

  .p-share {
      font-size: 13px;
      width: 200rpx;
      height: 80rpx;
      border: 1px solid #999999;
      margin: 20rpx;
      background-color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 13rpx;
  }

</style>
