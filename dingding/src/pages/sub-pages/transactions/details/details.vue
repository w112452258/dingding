<template>
  <div>
    <div class="content">
      <div class="my-container">
        <div class="top">
          <div class="top-left">
            <img class="img-top" :src="imgTop" />
          </div>
          <p class="p-top">{{ title }}</p>
        </div>
      </div>

      <div class="my-container">
        <div class="mid">
          <div class="desc">
            <div class="desc-top">
              <div class="img-mid">
                <img
                  class="img-head-portrait"
                  :src="imgMid"
                />
                <p class="p-name">{{ name }}</p>
              </div>
              <p class="p-telnum">{{ telnum }}</p>
            </div>
            <div class="desc-bottom">
              <p class="p-name">收货地址</p>
              <div class="desc-bottom-position">
                <p class="p-position">{{ city }}</p>
                <p class="p-position">{{ position }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="my-container">
        <div class="bottom">
          <div class="item">
            <p class="p-name">订单号</p>
            <p class="p-telnum">{{ orderNum }}</p>
          </div>
          <div class="item">
            <p class="p-name">金额</p>
            <p class="p-price">¥{{ price }}</p>
          </div>
          <div class="item">
            <p class="p-name">优惠</p>
            <p class="p-preferential">¥-{{ preferential }}</p>
          </div>
          <div class="item">
            <p class="p-name">优惠方式</p>
            <p class="p-telnum">{{ preferentialWay }}</p>
          </div>
          <div class="item">
            <p class="p-name">支付方式</p>
            <p class="p-telnum">{{ payWay }}</p>
          </div>
          <div class="item">
            <p class="p-name">交易号</p>
            <p class="p-telnum">{{ transaction }}</p>
          </div>
          <div class="item">
            <p class="p-name">配送方式</p>
            <p class="p-telnum">{{ delivery }}</p>
          </div>
          <div class="item">
            <p class="p-name">物流编号</p>
            <p class="p-telnum">{{ deliveryNum }}</p>
          </div>
          <div class="item">
            <p class="p-name">交易时间</p>
            <p class="p-telnum">{{ time }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { formatTime } from "@/utils/index";
import card from "@/components/card";

export default {
  components: {
    card
  },

  data() {
    return {
      imgTop: 'https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp',
      title: '嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品',
      imgMid: 'https://img.alicdn.com/tfscom/i4/743792891/O1CN01zfFm6Q1XE7YJPthqF_!!743792891.jpg_460x460xz.jpg',
      name: 'hussessf',
      telnum: '13845451245',
      city: '湖南省 - 株洲市',
      position: '天元区动力谷创新园ABCD区12栋3楼202室',
      orderNum: '45123456789104646',
      price: '152.00',
      preferential: '25.00',
      preferentialWay: '满100减25',
      payWay: '微信支付',
      transaction: '45123456789104646',
      delivery: '顺风物流',
      deliveryNum: 'FE456454546454',
      time: '2019-08-11 15:29:45'
    };
  },

  created() {
    let logs;
    if (mpvuePlatform === "my") {
      logs = mpvue.getStorageSync({ key: "logs" }).data || [];
    } else {
      logs = mpvue.getStorageSync("logs") || [];
    }
    this.logs = logs.map(log => formatTime(new Date(log)));
  }
};
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
  width: 100%;
  /* background-color: red; */
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  margin-bottom: 10rpx;
  background-color: #fff;
}

.top {
  width: 90%;
  height: 150rpx;
  display: flex;
  justify-content: center;
  align-items: center;
  /* padding: 20rpx 0; */
  /* background-color: #fff; */
  /* margin-bottom: 10rpx; */
}

.top-left {
  width: 20%;
  height: 100%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
}

.img-top {
  width: 110rpx;
  height: 110rpx;
  background-color: aqua;
}

.p-top {
  width: 80%;
  font-size: 13px;
  /* display: flex;
      align-self: flex-start; */
}

.mid {
  width: 90%;
  height: 260rpx;
  /* background-color: #fff; */
  display: flex;
  justify-content: center;
  align-items: center;
}

.desc {
  width: 100%;
  height: 240rpx;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
}

.desc-top {
  width: 100%;
  height: 50%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* background-color: #999999; */
  border-bottom: 1px solid #cccccc;
}

.img-mid {
  height: 100%;
  display: flex;
  align-items: center;
}

.img-head-portrait {
  width: 90rpx;
  height: 90rpx;
  background-color: aqua;
  border-radius: 45rpx;
  margin-right: 20rpx;
}

.p-name {
  /* width: 40%; */
  /* height: 100%; */
  font-size: 13px;
  display: flex;
  justify-content: flex-start;
}

.p-telnum {
  /* height: 100%; */
  font-size: 13px;
  color: #999999;
}

.desc-bottom {
  width: 100%;
  height: 50%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.desc-bottom-position {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: flex-end;
}

.p-position {
  font-size: 12px;
  color: #999999;
}

.bottom {
  width: 90%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.item {
  width: 100%;
  height: 80rpx;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid #e2e2e2;
}

.p-price {
  font-size: 13px;
  color: #ff0000;
}

.p-preferential {
  font-size: 13px;
  color: #cc6600;
}
</style>
