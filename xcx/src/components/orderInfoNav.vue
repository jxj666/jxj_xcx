<template>
  <div class="nav">
    <div class="line_c h1">

    </div>
    <div class="box">
      <span class="list1 first_c">订单总额
        <span class="theme_c">￥{{order.money*order.time}}</span>
      </span>
      <span class="list2 theme_bg_c" >提交订单</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["order"],
  data() {
    return {};
  },
  methods: {
 
  }
};
</script>

<style scoped lang='scss'>
.nav {
  position: fixed;
  bottom: 0;
  height: 90rpx;
  width: 100vw;
  background: #fff;
  .box {
    display: flex;
    justify-content: space-between;
    span {
      line-height: 90rpx;
    }
    .list1 {
      margin-left: 30rpx;
      padding: 0 30rpx 0 0;
      font-size: 30rpx;
    }
    .list2 {
      color: #fff;
      padding: 0 50rpx;
    }
 
  }
  .h1 {
    height: 1rpx;
  }
}
</style>
