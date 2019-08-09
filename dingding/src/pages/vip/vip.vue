<template>
  <div>
    <div class="content">
        <div class="vip" v-for="v in vip" :key="v.id">
            <div class="my-container">
                <div class="left">
                    <img class="img-vip" :src="v.imgUrl">
                    <div class="desc">
                        <p class="p-vip">{{ v.name }}</p>
                        <p class="p-vip">{{ v.num }}</p>
                    </div>
                </div>
                <div class="right">
                    <p class="p-vip">{{ v.rank }}</p>
                    <p class="p-time">{{ v.time }}</p>
                </div>
            </div>
        </div>
        <p class="add-vip">添加会员</p>
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
      vip: [
          {
              imgUrl: 'https://img.alicdn.com/tfscom/i4/743792891/O1CN01zfFm6Q1XE7YJPthqF_!!743792891.jpg_460x460xz.jpg',
              name: '哈哈哈',
              num: '13578784545',
              rank: '五星会员',
              time: '2018-08-12'
          },
          {
              imgUrl: 'https://img.alicdn.com/tfscom/i4/743792891/O1CN01zfFm6Q1XE7YJPthqF_!!743792891.jpg_460x460xz.jpg',
              name: '哈哈哈',
              num: '13578784545',
              rank: '五星会员',
              time: '2018-08-12'
          },
          {
              imgUrl: 'https://img.alicdn.com/tfscom/i4/743792891/O1CN01zfFm6Q1XE7YJPthqF_!!743792891.jpg_460x460xz.jpg',
              name: '哈哈哈',
              num: '13578784545',
              rank: '五星会员',
              time: '2018-08-12'
          }
      ]
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
    overflow: auto;
    padding-bottom: 120rpx;
  }

  .vip {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: #fff;
      padding: 20rpx 0;
      margin-bottom: 10rpx;
  }

  .my-container {
      width: 90%;
      display: flex;
      justify-content: space-between;
      align-items: center;
  }

  .left {
      display: flex;
      justify-content: flex-start;
      align-items: center;
  }

  .img-vip {
      width: 80rpx;
      height: 80rpx;
      background-color: aqua;
  }

  .desc {
      height: 80rpx;
      display: flex;
      flex-direction: column;
      justify-content: space-around;
      margin-left: 10rpx;
  }

  .p-vip {
      font-size: 13px;
  }

  .right {
      height: 80rpx;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      align-items: flex-end;
  }

  .p-time {
      font-size: 13px;
      color: #999999;
  }

  .add-vip {
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
