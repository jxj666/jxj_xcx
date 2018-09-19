<template>
  <div class="payInfo bg_c">
    <div class="topline line_c"></div>
    <div class="listbox fff_bg_c">
      <span class="second_c ">订单金额</span>
      <span class="theme_c">￥{{payInfo.money*payInfo.time}}</span>
    </div>

    <div class="h_10 bg_c"></div>

    <div class="fff_bg_c">
      <div class="listbox2 money">
        <h5 class="second_c ">
          <span class="first_c">额度支付</span>
        </h5>
        <p class="third_c">
          可用剩余额度 ￥10000</p>
      </div>
    </div>

    <div class="h_10 bg_c"></div>

    <pay-info-card :order='payInfo'></pay-info-card>

    <div class="h_10 bg_c"></div>

    <div class="listbox3">
      <span class="choice">&nbsp;</span>
      <span class="second_c ">我已阅读并同意 </span>
      <span class="first_c">《借款相关条款》</span>
    </div>
    <div class="bg_c h_100"></div>
    <pay-info-nav :order='payInfo'></pay-info-nav>
  </div>
</template>

<script>
import payInfoCard from "@/components/payInfoCard";
import payInfoNav from "@/components/payInfoNav";

export default {
  data() {
    return {
      payInfo: {}
    };
  },

  components: {
    payInfoCard,
    payInfoNav
  },

  methods: {
    getList() {
      this.payInfo = wx.getStorageSync("payInfo");
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
      title: "付款详情"
    });
  }
};
</script>

<style scoped lang="scss">
.payInfo {
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
    .listbox3 {
    font-size: 30rpx;
    line-height: 2;
    padding: 20rpx 30rpx;
    display: flex;
    justify-content:flex-start;

    &.option {
      background: url(../../../static/img/arrow.png) no-repeat 95vw center;
      background-size: 20rpx 20rpx;
      padding: 20rpx 60rpx 20rpx 20rpx;
    }
    span {
    }
        .choice {

      background: url(../../../static/img/yes.png) no-repeat center;
      background-size: 30rpx 30rpx;
      padding: 0 30rpx;
    }
  }
  .listbox2 {
    font-size: 30rpx;
    line-height: 2;
    padding: 20rpx 30rpx;
    &.money {
      background: url(../../../static/img/money.png) no-repeat 30rpx 42rpx;
      background-size: 30rpx 30rpx;
      padding: 20rpx 80rpx;
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
