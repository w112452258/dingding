<template>
  <div>
    <div class="content">
      <div class="my-container">
        <div class="commodity">
          <div class="commodity-left">
            <img
              class="img-commodity"
              src="https://img10.360buyimg.com/pop/s590x470_jfs/t1/61278/23/6442/71221/5d48d385Ec1439b9c/b9439c2e592359a5.jpg.webp"
            />
          </div>
          <div class="commodity-right">
            <p class="p-title">{{ title }}</p>
            <p class="p-type">{{ type }}</p>
            <div class="commodity-mid">
              <p class="p-num">评分：{{ num }}</p>
              <img class="img-like" :src="like_icon" v-for="ln in likeNum" :key="ln.id" />
            </div>
          </div>
        </div>

        <div class="evaluation-num">
          <p class="p-evaluation">总评({{ total }})</p>
          <p class="p-evaluation">好评({{ good }})</p>
          <p class="p-evaluation">中评({{ medium }})</p>
          <p class="p-evaluation">差评({{ bad }})</p>
        </div>

        <div class="evaluation" v-for="(e, index) in evaluation" :key="e.id">
          <div class="evaluation-top">
            <img
              class="img-portrait"
              :src="e.portrait"
            />
            <div class="desc">
              <div class="desc-top">
                <p class="p-name">{{ e.name }}</p>
                <img class="img-like" :src="like_icon" v-for="(eln, index1) in e.likeNum" :key="eln.id" />
              </div>
              <div class="desc-bottom">
                <p class="p-desc">{{ e.desc }}</p>
                <p class="p-desc">{{ e.time }}</p>
              </div>
            </div>
          </div>
          <div class="evaluation-mid">
            <p class="p-comment">{{ e.comment }}</p>
          </div>

          <div class="evaluation-bottom">
            <p class="p-reply">回复</p>
            <p class="p-reply">禁显</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { formatTime } from "@/utils/index";
import card from "@/components/card";
import { like_icon } from "./../../../../assets/icon";

export default {
  components: {
    card
  },

  data() {
    return {
      like_icon: like_icon,
      title: "嘉实多极护5W-40 全合成机油汽车润滑油SN级 4L每瓶 苏宁正品",
      type: "车品-美容",
      num: "4.9",
      likeNum: 5,
      total: "239",
      good: "201",
      medium: "18",
      bad: "20",
      evaluation: [
        {
          name: "Hu**lw",
          portrait: 'https://img.alicdn.com/tfscom/i4/743792891/O1CN01zfFm6Q1XE7YJPthqF_!!743792891.jpg_460x460xz.jpg',
          likeNum: 4,
          desc: "型号：W-40全合成机油",
          time: "2019-08-11 12:45:10",
          comment:
            "评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本"
        },
        {
          name: "Hu**lw",
          portrait: 'https://img.alicdn.com/tfscom/i4/743792891/O1CN01zfFm6Q1XE7YJPthqF_!!743792891.jpg_460x460xz.jpg',
          likeNum: 4,
          desc: "型号：W-40全合成机油",
          time: "2019-08-11 12:45:10",
          comment:
            "评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本评论内容，多行文本"
        },
        {
          name: "Hu**lw",
          portrait: 'https://img.alicdn.com/tfscom/i4/743792891/O1CN01zfFm6Q1XE7YJPthqF_!!743792891.jpg_460x460xz.jpg',
          likeNum: 5,
          desc: "型号：W-40全合成机油",
          time: "2019-08-11 12:45:10",
          comment:
            "评论内容，多行文本评论内容，多行文本评论内容，多行文本"
        }
      ]
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
  /* position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0; */
  background-color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  padding: 0;
  overflow: auto;
}

.my-container {
  width: 90%;
  /* background-color: red; */
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  /* padding: 20rpx 0; */
}

.commodity {
  width: 100%;
  height: 236rpx;
  display: flex;
  justify-content: center;
  align-items: center;
}

.commodity-left {
  width: 30%;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  /* background-color: aqua; */
}

.img-commodity {
  width: 190rpx;
  height: 190rpx;
}

.commodity-right {
  width: 70%;
  height: 190rpx;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

.p-title {
  font-size: 13px;
  margin-bottom: 10rpx;
}

.p-type {
  font-size: 12px;
  color: #999999;
  margin-bottom: 10rpx;
}

.commodity-mid {
  display: flex;
}

.p-num {
  width: 170rpx;
  font-size: 12px;
}

.img-like {
  width: 15px;
  height: 15px;
}

.evaluation-num {
  width: 100%;
  margin: 10rpx 0;
  display: flex;
  justify-content: flex-start;
  align-items: center;
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

.evaluation {
  width: 100%;
  /* height: 300rpx; */
  border-top: 1px solid #cccccc;
  padding: 10rpx 0;
  display: flex;
  flex-direction: column;
  margin-bottom: 10rpx;
  /* background-color: aqua; */
  /* justify-content: center; */
}

.evaluation-top {
  width: 100%;
  height: 90rpx;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.img-portrait {
  width: 80rpx;
  height: 80rpx;
  border-radius: 40rpx;
  /* background-color: red; */
}

.desc {
  width: 580rpx;
}

.desc-top {
  width: 100%;
  display: flex;
  align-items: center;
}

.p-name {
  margin-right: 10rpx;
}

.desc-bottom {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.p-desc {
  font-size: 12px;
  color: #999999;
}

.evaluation-mid {
  width: 100%;
  /* height: 170rpx; */
  display: flex;
  justify-content: flex-start;
  align-items: flex-start;
  padding: 20rpx 0;
}

.p-comment {
  font-size: 13px;
  text-overflow: -o-ellipsis-lastline;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
}

.evaluation-bottom {
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

.p-reply {
  width: 100rpx;
  height: 40rpx;
  background-color: #3399ff;
  text-align: center;
  line-height: 40rpx;
  font-size: 12px;
  color: #fff;
  padding: 0 6rpx;
  margin-right: 20rpx;
}
</style>
