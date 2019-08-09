<template>
  <div>
    <div class="content">
      <div class="settle" v-for="s in settle" :key="s.id">
        <div class="my-container">
          <div class="left">
            <img class="img-settle" :src="s.imgUrl">
          </div>
          <div class="mid">
            <p class="p-title">{{ s.title }}</p>
            <p class="p-time">{{ s.time }}</p>
          </div>
          <div class="right">
            <p class="p-num1" v-if="s.title==='提现'">-{{ s.num }}元</p>
            <p class="p-num2" v-if="s.title!=='提现'">+{{ s.num }}元</p>
          </div>
        </div>
      </div>
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
      settle: [
        {
          title: '提现',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp'
        },
        {
          title: '订单结算入账',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img12.360buyimg.com/babel/s590x470_jfs/t1/55456/39/6631/38740/5d4434a3E94c96202/0948cdbd22cd53b7.jpg.webp'
        },
        {
          title: '提现',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img30.360buyimg.com/pop/s590x470_jfs/t1/78601/30/5278/71955/5d36c0c6E03c7ef7e/a599124e5f72ab11.jpg.webp'
        },
        {
          title: '提现',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img30.360buyimg.com/pop/s590x470_jfs/t1/78601/30/5278/71955/5d36c0c6E03c7ef7e/a599124e5f72ab11.jpg.webp'
        },
        {
          title: '提现',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img30.360buyimg.com/pop/s590x470_jfs/t1/78601/30/5278/71955/5d36c0c6E03c7ef7e/a599124e5f72ab11.jpg.webp'
        },
        {
          title: '提现',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img30.360buyimg.com/pop/s590x470_jfs/t1/78601/30/5278/71955/5d36c0c6E03c7ef7e/a599124e5f72ab11.jpg.webp'
        },
        {
          title: '提现',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img30.360buyimg.com/pop/s590x470_jfs/t1/78601/30/5278/71955/5d36c0c6E03c7ef7e/a599124e5f72ab11.jpg.webp'
        },
        {
          title: '提现',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img30.360buyimg.com/pop/s590x470_jfs/t1/78601/30/5278/71955/5d36c0c6E03c7ef7e/a599124e5f72ab11.jpg.webp'
        },
        {
          title: '提现',
          time: '2019-08-01 09:26:18',
          num: '3000',
          imgUrl: 'https://img30.360buyimg.com/pop/s590x470_jfs/t1/78601/30/5278/71955/5d36c0c6E03c7ef7e/a599124e5f72ab11.jpg.webp'
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
  }

  .settle {
    width: 100%;
    display: flex;
    justify-content: center;
    background-color: #fff;
    margin-bottom: 10rpx;
    transition: all ease 0.25s;
  }

  .my-container {
    width: 90%;
    height: 140rpx;
    /* background-color: red; */
    display: flex;
    justify-content: space-between;
    padding: 20rpx 0;
  }

  .left {
    width: 20%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .img-settle {
    width: 130rpx;
    height: 130rpx;
    background-color: aqua;
  }

  .mid {
    width: 55%;
    height: 130rpx;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }

  .p-title {
    font-size: 13px;
  }

  .p-time {
    font-size: 12px;
  }

  .right {
    width: 20%;
    height: 130rpx;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .p-num1 {
    font-size: 13px;
    color: #ff0000;
  }

  .p-num2 {
    font-size: 13px;
    color: #009900;
  }

</style>
