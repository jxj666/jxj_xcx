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
    <goods-info-card :goods='goodsInfo'></goods-info-card>
    <div v-if="goodsInfo.free==1">
      <div class="bg_c h_10"></div>
      <div class="listbox">
        <span class="second_c">促销</span>
        <span class="theme_c">免息</span>
      </div>
    </div>

    <div class="bg_c h_10"></div>
    <div class="listbox option">
      <span class="second_c ">已选</span>
      <span class="second_c">版本 {{goodsInfo.verison}}</span>
    </div>
    <div class="bg_c h_1"></div>

    <div class="listbox option">
      <span class="second_c">送至</span>
      <span class="second_c">你的地址</span>
    </div>

    <div class="bg_c h_10"></div>
    <div class="listbox option">
      <span class="second_c">规格参数/包装售后</span>
    </div>

    <div class="bg_c h_10"></div>
    <div class="listbox">
      <div class="richText" :style="{'zoom':zoom}">
        <rich-text :nodes="page"></rich-text>
      </div>
    </div>

    <div class="bg_c h_100"></div>

    <goods-info-nav :goods='goodsInfo'></goods-info-nav>
  </div>
</template>

<script>
import goodsInfoCard from "@/components/goodsInfoCard";
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
      goodsInfo: {},
      page: " ",
      zoom: 1
    };
  },

  components: {
    goodsInfoCard,
    goodsInfoNav
  },

  methods: {
    getList() {
      this.goodsInfo = wx.getStorageSync("goodsInfo");
      var that = this;
      wx.request({
        url:
          "https://easy-mock.com/mock/5b1b95e6e4e8507ccf4dcd14/06/jxj/getProductInfo",
        methods: "get",
        success: res => {
          if (res.data.code == 0) {
            that.upList(res.data.data);
          } else {
            console.log("网络错误!");
          }
        }
      });
    },
    upList(data) {
      this.page = data.result.introduction;
    },
    getZoom() {
      var width = wx.getSystemInfoSync().windowWidth;
      console.log(width);
      this.zoom = width / 1000 * 1.26;
    }
  },

  created() {},
  onShow() {
    this.getZoom();
    this.getList();
  },
  onHide() {},
  onLoad: function() {
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
  .listbox {
    font-size: 30rpx;
    line-height: 2;
    padding: 20rpx 30rpx;
    display: flex;
    justify-content: space-between;

    &.option {
      background: url(../../../static/img/arrow.png) no-repeat 95vw center;
      background-size: 20rpx 20rpx;
      padding: 20rpx 60rpx 20rpx 20rpx;
    }
    span {
    }
  }
  .richText {
    width: 100vw;
    img {
      width: 100%;
    }
  }
  .h_100 {
    height: 100rpx;
  }
  .h_10 {
    height: 10rpx;
  }
  .h_1 {
    height: 1rpx;
  }
}
</style>
