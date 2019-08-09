<template>
  <div>
    <div class="content">
      <div class="transaction" v-for="t in transaction" :key="t.id" @click="details">
        <div class="my-container">
          <div class="left">
            <div class="num">
              <p class="p-desc">订单编号：{{ t.num }}</p>
            </div>
            <div class="name">
              <p class="p-desc">商品名称：{{ t.name }}</p>
            </div>
            <div class="price">
              <p class="p-desc">单价：{{ t.unitPrice }}</p>
              <p class="p-desc">总价：{{ t.totalPrice }}</p>
            </div>
            <div class="time">
              <p class="p-desc">交易时间：{{ t.time }}</p>
            </div>
          </div>
          <div class="right">
            <img class="img-more" :src="more1_icon">
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
    more1_icon
  } from './../../assets/icon'


export default {
  components: {
    card
  },

  data () {
    return {
      more1_icon: more1_icon,
      transaction: [
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
        },
        {
          num: '45454545454545454',
          name: '啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊啊',
          unitPrice: '128.00',
          totalPrice: '128.00',
          time: '2019-04-04 12:40:00'
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
    details() {
      wx.navigateTo({url: './../sub-pages/transactions/details/main'})
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

  .transaction {
    width: 100%;
    display: flex;
    justify-content: center;
    background-color: #fff;
    margin-bottom: 10rpx;
    transition: all ease 0.25s;
  }

  .transaction:active {
    background-color: rgb(246, 246, 246);
  }

  .my-container {
    width: 90%;
    height: 188rpx;
    /* background-color: red; */
    display: flex;
    padding: 20rpx 0;
  }

  .left {
    width: 90%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: flex-start;
  }

  .p-desc {
    font-size: 14px;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
  }

  .desc {
    width: 100%;
  }

  .num {
    width: 100%;
  }

  .name {
    width: 100%;
  }

  .price {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .time {
    width: 100%;
  }

  .right {
    width: 10%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .img-more {
    width: 20px;
    height: 20px;
  }

</style>
