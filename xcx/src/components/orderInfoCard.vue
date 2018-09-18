<template>
  <div class="order fff_bg_c">
    <img :src="order.url" alt="order.url">
    <div class="listBox">
      <h3 class="first_c">{{order.title}}</h3>
      <h5 class="second_c ">
        <span class="">&nbsp;版本{{order.verison}}&nbsp;</span>
      </h5>
      <p class="theme_c">￥{{order.money*order.time}}</p>
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
.order {
  // height: 150rpx;
  padding: 5vw ;
  position: relative;

  img {
    width: 40vw;
    height: 40vw;
    box-sizing: border-box;
    border: 1rpx solid #ededf0;
  }
  .listBox {
    width: 50vw;
    // height: 170rpx;
    box-sizing: border-box;
    position: absolute;
    top: 5vw;
    right: 0;
  }
  p {
    margin: 40rpx 0 0;
    font-size: 40rpx;
    line-height: 1.5;
  }
  h3 {
    margin-top: 5rpx;
    font-size: 35rpx;
    line-height: 1.5;
    height: 105rpx;
  }
  h5 {
    font-size: 25rpx;
    line-height: 1.5;
    height: 75rpx;
  }
  
}
</style>
