<template>
  <div class="goods" >
    <img :src="goods.url" alt="goods.url">
    <div class="listBox">
    <h3 class="first_c">{{goods.title}}</h3>
    <h5 class="second_c "><span class="bg_c">&nbsp;版本{{goods.verison}}&nbsp;</span></h5>
    <p class="theme_c">￥{{goods.money*goods.time}}</p>
    <P class="fist_c"><span class="theme_c">￥{{goods.money}}</span>×{{goods.time}}期</P>
    <div class="btn" v-if="goods.free"><span class="bg_c theme_c">&nbsp;免息&nbsp;</span></div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["goods"],
  data() {
    return {};
  },
  methods: {
   
  }
};
</script>

<style scoped lang='scss'>
.goods { 
  height: 150rpx;
  padding: 10rpx;
  position: relative;
 
  img {
    width: 150rpx;
    height: 150rpx;
    box-sizing: border-box;
    border: 1rpx solid #ededf0;
  }
  .listBox{
    width: 75vw;
    height: 170rpx;
    padding: 10rpx 0;
    box-sizing: border-box;
    position: absolute;
    top: 0;
    right: 0;
  }
  p {
    font-size: 20rpx;
    line-height: 1.5;
    
  }
  h3{
    margin-top: 5rpx;
    font-size: 30rpx;
    line-height: 1.5;
  }
  h5{
    font-size: 25rpx;
    line-height: 1.5;
  }
  .btn{
    position: absolute;
    bottom:  50rpx;
    right: 50rpx;
    span{
      line-height: 1.5;
      font-size: 25rpx;
    }
  }
}
</style>
