<template>
  <div class="box" :class="{activity:activity}" @click="choiceType">
    <h5 class="first_c">{{x}}期</h5>
    <p class="second_c">月供: ￥{{fix_money}}</p>
    <h3 class="theme_bg_c">免息</h3>
  </div>
</template>

<script>
export default {
  props: ["order", "x", "activity"],
  data() {
    return {};
  },
  computed: {
    fix_money() {
      return parseInt(this.order.money * this.order.time / this.x);
    }
  },
  methods: {
    choiceType() {
      this.$emit("choiceType", this.x);
    }
  }
};
</script>

<style scoped lang='scss'>
.box {
  text-align: center;
  padding: 20rpx;
  position: relative;
  border: 1rpx solid #ededf0;
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  border-radius: 10rpx;
  h5 {
    font-size: 30rpx;
    line-height: 2;
  }
  p {
    font-size: 25rpx;
    line-height: 1.5;
  }
  h3 {
    padding: 0 5rpx;
    position: absolute;
    top: -10rpx;
    right: -10rpx;
    color: #fff;
    font-size: 25rpx;
    border-radius: 5rpx;
  }
  &.activity {
    border: 1px solid #ff142d;
    p,
    h5 {
      color: #ff142d;
    }
  }
}
</style>
