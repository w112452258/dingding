<template>
  <div class="content">
    <textarea class="text-Announcement" name="textarea" focus="true" :show-confirm-bar="false" maxlength="-1"></textarea>
    <p class="add-announcement" @click="announcement">添加公告</p>
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
    return {};
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
    announcement() {
      wx.navigateBack({
        delta: 1
      });
    }
  }
};
</script>

<style scoped>
.content {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  padding: 0;
  overflow-y: auto;
}

.text-Announcement {
  width: 90%;
  height: 900rpx;
  /* background-color: aqua; */
  /* border-bottom: 1px solid #cccccc; */
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
  /* position: fixed;
    bottom: 20rpx; */
  margin: 50rpx 0;
}

</style>
