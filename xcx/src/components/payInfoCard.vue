<template>
  <div class="pay fff_bg_c">
    <div class="listbox">
      <span class="first_c">
        分期方案&nbsp;
        <span class="second_c">(如有逾期收取当期利息及服务费)</span>
      </span>
    </div>
    <div class="choicebox">
      <div class="choice" v-for="x in choicebox">
        <pay-choice :order='order' :x='x' :activity='x==type' @choiceType='choiceType'></pay-choice>

      </div>
    </div>
    <div class="h_1 bg_c"></div>
    <div class="listbox alert">
      <span class="first_c">
        每期需还
      </span>
      <span class="theme_c">￥{{fix_money}}</span>
    </div>
  </div>
</template>

<script>
import payChoice from "@/components/payChoice";
export default {
  props: ["order"],
  data() {
    return {
      choicebox: [1, 3, 6, 9, 12, 24],
      type: 1
    };
  },
  computed: {
    fix_money() {
      return parseInt(this.order.money * this.order.time / this.type);
    }
  },
  components: {
    payChoice
  },
  methods: {
    choiceType(x) {
      this.type = x;
    }
  }
};
</script>

<style scoped lang='scss'>
.pay {
  // height: 150rpx;
  position: relative;
  .listbox {
    font-size: 30rpx;
    line-height: 2;
    padding: 20rpx 30rpx;
    display: flex;
    justify-content: space-between;
    &.option {
      background: url(../../static/img/arrow.png) no-repeat 95vw center;
      background-size: 20rpx 20rpx;
      padding: 20rpx 60rpx 20rpx 20rpx;
    }
    &.alert {
      background: url(../../static/img/alert.png) no-repeat 90vw center;
      background-size: 30rpx 30rpx;
      padding: 20rpx 100rpx 20rpx 20rpx;
    }

    span {
    }
  }
  .choicebox {
    overflow: auto;
    .choice {
      float: left;
      margin-left: 2.5vw;
      margin-top: 1vw;
      margin-bottom: 2.5vw;
      width: 30vw;
      height: 20vw;
    }
  }
}
</style>
