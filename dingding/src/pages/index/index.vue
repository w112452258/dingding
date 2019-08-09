<template>

    <div class="content">
      <div class="header">
        <div class="my-container">
          <div class="header-content">
            <div class="header-item">
              <p class="p-header-mid">今日已收款/元</p>
              <p class="p-header-bottom num">{{ income }}</p>
            </div>
            <div class="header-item1">
              <p class="p-header-mid">查看详情</p>
              <img class="img-more" :src="more1_icon">
            </div>
          </div>
          <div class="header-content">
            <div class="header-item2">
              <p class="p-header-bottom num">{{ newOrder }}</p>
              <p class="p-header-mid">新订单</p>
            </div>
            <div class="header-item2">
              <p class="p-header-bottom num">{{ todayOrder }}</p>
              <p class="p-header-mid">今日订单</p>
            </div>
            <div class="header-item2">
              <p class="p-header-bottom num">{{ Balance }}</p>
              <p class="p-header-mid">账户余额</p>
            </div>
          </div>

        </div>
      </div>

      <div class="recording">
        <div class="my-container">
          <div class="recording-item">
            <div class="record-item">
              <img class="img-item" :src="writeOff_icon">
              <p class="p-recording">卡券核销</p>
            </div>
            <div class="record-item" @click="transaction">
              <img class="img-item" :src="transaction_icon">
              <p class="p-recording">交易记录</p>
            </div>
            <div class="record-item" @click="settle">
              <img class="img-item" :src="settle_icon">
              <p class="p-recording">结算记录</p>
            </div>
          </div>
        </div>
      </div>

      <div class="management">
        <div class="my-container">
          <p>门店管理</p>
          <div class="management-item">
            <div class="item" @click="shop">
              <img class="img-item" :src="shop_icon">
              <p class="p-recording">店铺管理</p>
            </div>
            <div class="item" @click="commodity">
              <img class="img-item" :src="commodity_icon">
              <p class="p-recording">商品管理</p>
            </div>
            <div class="item" @click="order">
              <img class="img-item" :src="order_icon">
              <p class="p-recording">订单评价</p>
            </div>
            <div class="item">
              <img class="img-item" :src="finance_icon">
              <p class="p-recording">财务对账</p>
            </div>
          </div>
        </div>
      </div>

      <div class="operation">
        <div class="my-container">
          <p>门店运营</p>
          <div class="operation-item">
            <div class="operation-item1">
              <div class="item" @click="promotion">
                <img class="img-item" :src="promotion_icon">
                <p class="p-recording">店铺推广</p>
              </div>
              <div class="item">
                <img class="img-item" :src="activity_icon">
                <p class="p-recording">活动配置</p>
              </div>
              <div class="item" @click="announcement">
                <img class="img-item" :src="announcement_icon">
                <p class="p-recording">店铺公告</p>
              </div>
              <div class="item">
                <img class="img-item" :src="report_icon">
                <p class="p-recording">报表数据</p>
              </div>
            </div>
            <div class="operation-item2">
              <div class="item" @click="vip">
                <img class="img-item" :src="vip_icon">
                <p class="p-recording">会员管理</p>
              </div>
              <div class="item" @click="production">
                <img class="img-item" :src="production_icon">
                <p class="p-recording">卡券制作</p>
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
    writeOff_icon,
    transaction_icon,
    settle_icon,
    shop_icon,
    commodity_icon,
    order_icon,
    finance_icon,
    promotion_icon,
    activity_icon,
    announcement_icon,
    report_icon,
    vip_icon,
    production_icon ,
    more1_icon
  } from './../../assets/icon'


export default {
  components: {
    card
  },

  data () {
    return {
      // test_icon: test_icon,
      // logs: [],
      // imgUrls: [
      //   'http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/newsPicture/05558951-de60-49fb-b674-dd906c8897a6',
      //   'http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/coursePicture/0fbcfdf7-0040-4692-8f84-78bb21f3395d',
      //   'http://mss.sankuai.com/v1/mss_51a7233366a4427fa6132a6ce72dbe54/management-school-picture/7683b32e-4e44-4b2f-9c03-c21f34320870'
      // ]
      income: '8405.00',
      newOrder: '3',
      todayOrder: '56',
      Balance: '5682.00',
      writeOff_icon: writeOff_icon,
      transaction_icon: transaction_icon,
      settle_icon: settle_icon,
      shop_icon: shop_icon,
      commodity_icon: commodity_icon,
      order_icon: order_icon,
      finance_icon: finance_icon,
      promotion_icon: promotion_icon,
      activity_icon: activity_icon,
      announcement_icon: announcement_icon,
      report_icon: report_icon,
      vip_icon: vip_icon,
      production_icon: production_icon,
      more1_icon: more1_icon
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
    transaction() {
      wx.navigateTo({url: './../transaction/main'})
    },
    
    settle() {
      wx.navigateTo({url: './../settle/main'})
    },

    shop() {
      wx.navigateTo({url: './../shop/main'})
    },

    commodity() {
      wx.navigateTo({url: './../commodity/main'})
    },

    order() {
      wx.navigateTo({url: './../order/main'})
    },

    promotion() {
      wx.navigateTo({url: './../promotion/main'})
    },

    announcement() {
      wx.navigateTo({url: './../announcement/main'})
    },
    
    vip() {
      wx.navigateTo({url: './../vip/main'})
    },

    production() {
      wx.navigateTo({url: './../production/main'})
    },

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

  .my-container {
    width: 90%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    margin: 10px;
  }

  .header {
    width: 100%;
    height: 130px;
    display: flex;
    justify-content: center;
    background-color: #3399ff;
  }

  /* .header-top {

  } */

  .title {
    color: #fff;

  }

  .header-content {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 10px 0;
  }

  .header-item {
    /* width: 150rpx; */
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .header-item1 {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .header-item2 {
    width: 120rpx;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .p-header-mid {
    color: #fff;
    font-size: 13px;
  }

  .p-header-bottom {
    color: #fff;

  }

  .recording-item {
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-content: center;
  }

  .record-item {
    width: 150rpx;
    height: 130rpx;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    /* margin-top: 15px; */
    margin: 0 20rpx;
    border: 1px solid #fff;
    transition: all ease 0.25s;
  }

  .record-item:active {
    background-color: #f2f2f2;
    border: 1px solid #ddd;
  }

  .item {
    width: 150rpx;
    height: 130rpx;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 15px;
    border: 1px solid #fff;
    transition: all ease 0.25s;
  }

  .item:active {
    background-color: #f2f2f2;
    border: 1px solid #ddd;
  }
  
  .recording {
    width: 100%;
    height: 80px;
    background-color: #fff;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .img-item {
    width: 35px;
    height: 35px;
    /* background-color: black; */
  }

  .p-recording {
    font-size: 13px;
  }

  .management {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 10px;
    background-color: #fff;
  }

  .management-item {
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-items: center;
  }

  .operation {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 10px 0;
    background-color: #fff;
  }

  .operation-item {
    width: 100%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-wrap: wrap;
  }

  .operation-item1 {
    width: 100%;
    display: flex;
    justify-content: space-around;
    align-items: center;
  }

  .operation-item2 {
    width: 50%;
    display: flex;
    justify-content: space-around;
  }

  .num {
    font-weight: 700;
    margin-top: 10rpx;
  }

  .img-more {
    width: 30rpx;
    height: 30rpx;
    margin-left: 5rpx;
  }


</style>
