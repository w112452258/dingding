<template>
  <div>
    <div class="content">
        <div class="announcement" v-for="a in announcement" :key="a.id">
            <div class="my-container">
                <p class="p-announcement">{{ a.pAnnouncement }}</p>
                <p class="p-time">{{ a.time }}</p>
            </div>
        </div>
        <p class="add-announcement">添加公告</p>
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
      announcement: [
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
          },
          {
              pAnnouncement: '两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本两行文本',
              time: '2018-08-08 12:23:12'
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

  .announcement {
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
      flex-direction: column;
      justify-content: space-around;
      align-items: center;
  }

  .p-announcement {
      font-size: 13px;
      /* height: 26px; */
      /* color: #999999; */
      text-overflow: -o-ellipsis-lastline;
      overflow: hidden;
      text-overflow: ellipsis;
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
  }

  .p-time {
      width: 100%;
      font-size: 12px;
      color: #999999;
      display: flex;
      justify-content: flex-end;
  }

  .add-announcement {
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
