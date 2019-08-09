<template>
  <div>
    <div class="content">
        <div class="production" v-for="p in production" :key="p.id">
            <div class="my-container">
                <img class="img-production" src="">

                <p class="p-ticket">{{ p.ticket}}</p>
                <p class="p-time">有效期：{{ p.time1 }} 至 {{ p.time2 }}</p>

            </div>
        </div>
        <p class="add-production">卡券制作</p>
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
      production: [
          {
              ticket: '满100减50',
              time1: '2018-10-01',
              time2: '2019-10-01'
          },
          {
              ticket: '满100减50',
              time1: '2018-10-01',
              time2: '2019-10-01'
          },
          {
              ticket: '满100减50',
              time1: '2018-10-01',
              time2: '2019-10-01'
          },
          {
              ticket: '满100减50',
              time1: '2018-10-01',
              time2: '2019-10-01'
          },
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

  .production {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-top: 30rpx;
  }

  .my-container {
      width: 90%;
      height: 290rpx;
      position: relative;
      display: flex;
      flex-direction: column;
      align-items: center;
  }

  .img-production {
      width: 100%;
      height: 290rpx;
      background-color: aqua;
  }

  .p-ticket {
      font-size: 19px;
      font-weight: 700;
      position: absolute;
      top: 130rpx;
  }

  .p-time {
      font-size: 13px;
      position: absolute;
      bottom: 10rpx;
  }

  .add-production {
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
