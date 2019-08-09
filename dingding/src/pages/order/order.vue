<template>
  <div>
    <div class="content">
        <div class="order" v-for="o in order" :key="o.id" @click="evaluation">
            <div class="my-container">
                <div class="left">
                    <img class="img-order" :src="o.imgUrl">
                </div>
                <div class="right">
                    <p class="p-title">{{ o.title }}</p>
                    <p class="p-type">{{ o.type }}</p>
                    <div class="mid">
                        <p class="p-num">评分：{{ o.num }}</p>
                        <img class="img-like" :src="like_icon">
                        <img class="img-like" :src="like_icon">
                        <img class="img-like" :src="like_icon">
                    </div>
                    <div class="bottom">
                        <p class="p-evaluation">总评({{ o.total }})</p>
                        <p class="p-evaluation">好评({{ o.good }})</p>
                        <p class="p-evaluation">中评({{ o.medium}})</p>
                        <p class="p-evaluation">差评({{ o.bad }})</p>
                    </div>
                </div>
            </div>
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
      like_icon: like_icon,
      order: [
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '4.9',
              total: '239',
              good: '201',
              medium: '18',
              bad: '20'
          },
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '4.9',
              total: '255',
              good: '198',
              medium: '25',
              bad: '30'
          },
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '4.9',
              total: '210',
              good: '200',
              medium: '10',
              bad: '16'
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
  },

  methods: {
    evaluation() {
      wx.navigateTo({url: './../sub-pages/orders/evaluation/main'})
    },
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
  }

  .order {
    width: 100%;
    height: 236rpx;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #fff;
    margin-bottom: 10rpx;
    transition: all ease 0.25s;
  }

  .order:active {
    background-color: rgb(246, 246, 246);
  }

  .my-container {
    width: 90%;
    /* background-color: red; */
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20rpx 0;
  }

  .left {
      width: 30%;
      display: flex;
      justify-content: flex-start;
      align-items: center;
      /* background-color: aqua; */
  }

  .img-order {
      width: 190rpx;
      height: 190rpx;
  }

  .right {
      height: 190rpx;
      margin-left: 20rpx;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-content: space-between;
      /* background-color: #ff0000 */
  }

  .p-title {
      font-size: 13px;
  }

  .p-type {
      font-size: 12px;
      color: #999999;
      /* margin: 20rpx 0; */
  }

  .mid {
      display: flex;
      justify-content: flex-start;
      align-items: flex-end;
      /* margin: 10rpx 0; */
  }

  .p-num {
      width: 170rpx;
      font-size: 12px;
  }

  .img-like {
      width: 15px;
      height: 15px;
  }
  
  .bottom {
      display: flex;
  }

  .p-evaluation {
      width: 90rpx;
      height: 30rpx;
      background-color: #fd7070;
      /* display: flex; */
      text-align: center;
      line-height: 30rpx;
      font-size: 20rpx;
      color: #fff;
      padding: 0 6rpx;
      margin-right: 10rpx;
  }


</style>
