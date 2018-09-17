<template>
  <div class="nav">
    <div class="line_c h1">

    </div>
    <div class="box">
      <span class="list1 first_c">月供
        <span class="theme_c">￥{{goods.money}}</span>
      </span>
      <span class="list3"></span>
      <span class="list2 theme_bg_c">立即购买</span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["goods"],
  data() {
    return {};
  },
  methods: {}
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
      padding:0 30rpx 0 0;
      border-right: 1rpx solid #ededf0;
      font-size: 30rpx;
    }
    .list2{
      color: #fff;
      padding: 0 50rpx ;
    }
    .list3{
      padding: 0 50rpx;
      background: url(../../static/img/service.png) no-repeat center;
      background-size: 50rpx;
    }
  }
  .h1 {
    height: 1rpx;
  }
}
</style>
