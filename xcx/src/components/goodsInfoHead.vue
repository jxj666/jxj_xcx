<template>
  <div class="goods">
    
    <div class="moneyBox">

    <p class="theme_c price">￥{{goods.money*goods.time}}</p>

    <P class="fist_c mortgage">
      <span class="theme_c">￥{{goods.money}}</span>×{{goods.time}}期
    </P>
    </div>


    <h3 class="first_c">{{goods.title}}</h3>
    <h5 class="second_c">{{goods.title}}是一款相当好的产品! 隆重推荐! </h5>

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
.goods {
  padding: 20rpx;
  position: relative;

  p {
    line-height: 2;
  }
  .price {
  }
  .mortgage {
  }
  h3 {
    line-height: 1.5;
    font-size: 30rpx;
  }
  h5 {
    line-height: 1.5;
    font-size: 25rpx;
  }
  .moneyBox{
    display: flex;
    justify-content: space-between;
  }
}
</style>
