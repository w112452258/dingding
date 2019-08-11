<template>
  <div>
    <div class="content">
        <div class="recording" v-for="(r, index) in recording" :key="index">
            <div class="my-container">
                <div class="left">
                    <img class="img-recording" :src="r.imgUrl">
                </div>
                <div class="right">
                    <p class="p-title">{{ r.title }}</p>
                    <div class="mid">
                        <div class="desc">
                            <p class="p-type">{{ r.type }}</p>
                            <p class="p-num">{{ r.num }}</p>
                        </div>
                        <div class="operating">
                            <p class="p-operating">{{ r.operating }}</p>
                        </div>
                    </div>
                    <div class="bottom">
                        <p class="p-preferential" v-for="(rp, index1) in r.preferential" :key="index1">{{ rp }}</p>
                    </div>
                </div>
            </div>
        </div>

        <p class="add-commodity" @click="commodity">添加商品</p>
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
      recording: [
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '125.00',
              operating: '下架',
              preferential: [ '满100减20', '会员85折' ]
          },
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '125.00',
              operating: '上架',
              preferential: [ '满100减20', '会员85折' ]
          },
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '125.00',
              operating: '下架',
              preferential: [ '满100减20', '会员85折' ]
          },
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '125.00',
              operating: '下架',
              preferential: [ '满100减20', '会员85折' ]
          },
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '125.00',
              operating: '下架',
              preferential: [ '满100减20', '会员85折' ]
          },
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '125.00',
              operating: '下架',
              preferential: [ '满100减20', '会员85折' ]
          },
          {
              title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
              imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
              type: '车品-美容',
              num: '125.00',
              operating: '下架',
              preferential: [ '满100减20', '会员85折' ]
          },
          // {
          //     title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
          //     imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
          //     type: '车品-美容',
          //     num: '125.00',
          //     operating: '下架',
          //     preferential: [ '满100减20', '会员85折' ]
          // },
          // {
          //     title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
          //     imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
          //     type: '车品-美容',
          //     num: '125.00',
          //     operating: '下架',
          //     preferential: [ '满100减20', '会员85折' ]
          // },
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
      commodity() {
        wx.navigateTo({url: './../sub-pages/commoditys/addCommoditys/main'})
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
    overflow-y: auto;
    padding-bottom: 120rpx;
  }

  .recording {
    width: 100%;
    height: 240rpx;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #fff;
    margin-bottom: 10rpx;
    transition: all ease 0.25s;
    box-sizing: border-box;
    padding: 12rpx 0
  }

  .my-container {
    width: 90%;
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

  .img-recording {
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

  .mid {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      margin: 10rpx 0;
  }

  .desc {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
  }

  .p-type {
      font-size: 12px;
      color: #999999;
      margin-bottom: 10rpx;
  }

  .p-num {
      font-size: 12px;
      color: #ff0000;
  }

  .operating {
      width: 100rpx;
      height: 50rpx;
      background-color: #3399ff;
      display: flex;
      justify-content: center;
      align-items: center;
  }

  .p-operating {
      color: #fff;
      font-size: 12px;
  }

  .bottom {
      display: flex;

  }

  /* .preferential {
        
  } */

  .p-preferential {
      width: 110rpx;
      height: 30rpx;
      background-color: #cc66ff;
      /* display: flex; */
      text-align: center;
      line-height: 30rpx;  
      font-size: 20rpx;
      color: #fff;
      padding: 0 6rpx;
      margin-right: 10rpx;
  }

  .add-commodity {
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
