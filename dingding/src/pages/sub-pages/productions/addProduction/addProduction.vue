<template>
  <div>
    <div class="content">
      <div class="addproduction">
        <div class="my-container">
          <p class="p-preview">预览</p>
          <div class="production">
            <img class="test" :src="aaa" />
            <p class="p-name">{{ name }}</p>
            <p class="p-time">有效期：{{ dateStart }} 至 {{ dateEnd }}</p>
          </div>
        </div>
      </div>

      <div class="addproduction">
        <div class="my-container">
          <div class="item" @click="chooseImage">
            <p class="p-title">背景图</p>
            <p class="p-content">选择上传</p>
          </div>
          <div class="item">
            <p class="p-title">卡券名称</p>
            <input type="text" class="input-name" v-model.lazy="name" />
          </div>
          <div class="item">
            <p class="p-title">优惠规则</p>
            <p class="p-content">满减优惠</p>
          </div>
          <div class="item">
            <p class="p-title">开始日期</p>
            <picker
              mode="date"
              :value="dateStart"
              start="2018-09-01"
              end="2025-09-01"
              @change="bindDateStartChange"
            >
              <p class="p-content">{{ dateStart }}</p>
            </picker>
          </div>
          <div class="item">
            <p class="p-title">结束日期</p>
            <picker
              mode="date"
              :value="dateEnd"
              :start="dateStart"
              end="2025-09-01"
              @change="bindDateEndChange"
            ><p class="p-content">{{ dateEnd }}</p></picker>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- <p @click="chooseImage">选择图片</p>
  <img class="test" :src="aaa" />-->
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
      aaa:
        "https://img.alicdn.com/tps/i4/TB1DLMacrr1gK0jSZFDSuv9yVXa.jpg_q90_.webp",
      name: "满150减20",
      dateStart: "2016-09-01",
      dateEnd: "2020-09-01"
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
  },

  methods: {
    chooseImage() {
      let that = this;
      wx.chooseImage({
        count: 1,
        sizeType: ["original", "compressed"],
        sourceType: ["album", "camera"],
        success(res) {
          // tempFilePath可以作为img标签的src属性显示图片
          that.aaa = res.tempFilePaths;
        }
      });
      // this.aaa = a,
      // console.log(this.aaa)
    },

    bindDateStartChange(e) {
      this.dateStart = e.mp.detail.value;
    },

    bindDateEndChange(e) {
      this.dateEnd = e.mp.detail.value;
    }
  }
};
</script>

<style scoped>
.test {
  width: 100%;
  height: 290rpx;
  /* background-color: aqua; */
}

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

.addproduction {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #fff;
  margin-bottom: 10rpx;
  padding: 20rpx 0;
}

.my-container {
  width: 90%;
  position: relative;
  /* padding: 20rpx 0; */
}

.production {
  display: flex;
  justify-content: center;
}

.p-preview {
  font-size: 14px;
  margin-bottom: 10rpx;
}

.p-name {
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

.item {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20rpx 0;
  border-bottom: 1px solid #cccccc;
}

.p-title {
  font-size: 13px;
}

.input-name {
  text-align: right;
  color: #999999;
}

.p-content {
  font-size: 13px;
  color: #999999;
}

</style>
