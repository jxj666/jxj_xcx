<template>
  <div class="orderInfo bg_c">
    <div class="topline line_c"></div>
    <div class="fff_bg_c">
      <div class="listbox2  option">
        <h5 class="second_c ">
          <span class="first_c">有熊小健</span>
          <span class="second_c">1880918001</span>
        </h5>
        <p class="third_c">
          <span class="icon">&nbsp;</span>北京市海淀区清华科技园启迪科技大厦</p>
      </div>
    </div>

    <div class="h10 bg_c"></div>
    <order-info-card :order='orderInfo'></order-info-card>
    <div class="h10 bg_c"></div>
    <div class="listbox fff_bg_c">
      <span class="second_c ">商品价格</span>
      <span class="second_c">￥{{orderInfo.money*orderInfo.time}}</span>
    </div>
    <div class="bg_c h1"></div>
    <div class="listbox fff_bg_c">
      <span class="second_c ">运费</span>
      <span class="second_c">免运费</span>
    </div>
    <div class="bg_c h1"></div>
    <div class="listbox fff_bg_c">
      <span class="second_c ">已选</span>
      <span class="theme_c">￥{{orderInfo.money*orderInfo.time}}</span>
    </div>
    <div class="bg_c h1"></div>
    <order-info-nav :order='orderInfo'></order-info-nav>
  </div>
</template>

<script>
import orderInfoCard from "@/components/orderInfoCard";
import orderInfoNav from "@/components/orderInfoNav";

export default {
  data() {
    return {
      orderInfo: {}
    };
  },

  components: {
    orderInfoCard,
    orderInfoNav
  },

  methods: {
    getList() {
      this.orderInfo = wx.getStorageSync("goodsInfo");
      var that = this;
    }
  },

  created() {},
  onShow() {
    this.getList();
  },
  onHide() {},
  onLoad: function() {
    wx.setNavigationBarTitle({
      title: "订单详情"
    });
  }
};
</script>

<style scoped lang="scss">
.orderInfo {
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
  .listbox2 {
    font-size: 30rpx;
    line-height: 2;
    padding: 20rpx 30rpx;
    &.option {
      background: url(../../../static/img/arrow.png) no-repeat 95vw center;
      background-size: 20rpx 20rpx;
      padding: 20rpx 60rpx 20rpx 20rpx;
    }
    span {
      margin-right: 10rpx;
    }
    h5 {
      font-size: 35rpx;
      line-height: 2;
    }
    p {
      font-size: 30rpx;
      line-height: 1.5;
      .icon {
        padding: 0 10rpx;
        background: url(../../../static/img/address.png) no-repeat center;
        background-size: 30rpx 30rpx;
      }
    }
  }
  .h100 {
    height: 100rpx;
  }
  .h10 {
    height: 10rpx;
  }
  .h1 {
    height: 1rpx;
  }
}
</style>
