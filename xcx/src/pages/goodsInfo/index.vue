<template>
  <div class="goodsInfo">
    <div class="topline line_c"></div>
    <div class="swiper">
      <swiper v-if="imgUrls.length>0" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration" :circular='circular' :indicatorDots='true'>
        <block :key='i' v-for="(x,i) in imgUrls">
          <swiper-item>
            <image :src="x" class="slide-image" />
          </swiper-item>
        </block>
      </swiper>
    </div>
    <goods-info-head :goods='goodsInfo'></goods-info-head>
    <div class="bg_c h10"></div>
  </div>
</template>

<script>
import goodsInfoBody from "@/components/goodsInfoBody";
import goodsInfoHead from "@/components/goodsInfoHead";
import goodsInfoNav from "@/components/goodsInfoNav";

export default {
  data() {
    return {
      indicatorDots: false,
      autoplay: false,
      interval: 5000,
      duration: 1000,
      circular: true,
      imgUrls: [
        "https://i8.mifile.cn/v1/a1/7da4043a-1b7d-72af-6d1c-c0ffca364f07.webp",
        "https://i8.mifile.cn/v1/a1/b523499a-ec22-37fc-8165-a1f5eae1e82c.webp",
        "https://i8.mifile.cn/v1/a1/a64944d5-3213-66f0-395d-c11229cfc6f1.webp"
      ],
      goodsInfo: {}
    };
  },

  components: {
    goodsInfoBody,
    goodsInfoHead,
    goodsInfoNav
  },

  methods: {
    getList() {
      this.goodsInfo = wx.getStorageSync("goodsInfo");
      var that = this;
      return;
      wx.request({
        url:
          "https://easy-mock.com/mock/5b9b68d11615c53f58edfeda/getGoodsClass",
        methods: "get",
        success: res => {
          if (res.data.code == 1) {
            that.upList(res.data.data);
          } else {
            console.log("网络错误!");
          }
        }
      });
    },
    upList(data) {}
  },

  created() {},
  onShow() {
    this.getList();
  },
  onHide() {
    this.listData.goodsList = [];
  },
  onLoad: function() {
    this.listData.goodsList = [];

    wx.setNavigationBarTitle({
      title: "商品详情"
    });
  }
};
</script>

<style scoped lang="scss">
.goodsInfo {
  width: 100vw;
  min-height: 100vh;
  position: relative;

  .topline {
    height: 1rpx;
    width: 100vw;
    position: fixed;
    top: 0;
    left: 0;
    overflow: hidden;
    z-index: 100;
  }
  .swiper {
    swiper {
      width: 100vw;
      height: 100vw;
      image {
        width: 100%;
        height: 100%;
      }
    }
  }
  .h10{
    height: 10rpx;
  }
}
</style>
