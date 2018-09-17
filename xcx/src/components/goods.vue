<template>
  <div class="goods" @click="toGoodsClass">
    <img :src="goods.url" alt="goods.url">
    <p class="first_c">{{goods.title}}</p>
  </div>
</template>

<script>
export default {
  props: ["goods"],
  data() {
    return {};
  },
  methods: {
    toGoodsClass() {
      wx.setStorageSync('goodsClass', this.goods)
      wx.navigateTo({
        url: `../goodsClass/main?title=${this.goods.title}`
      });
    }
  }
};
</script>

<style scoped lang='scss'>
.goods {
  img {
    width: 150rpx;
    height: 150rpx;
    box-sizing: border-box;
    border: 1rpx solid #ededf0;
  }
  p {
    font-size: 20rpx;
    text-align: center;
    line-height: 50rpx;
    margin-bottom: 10rpx;
  }
}
</style>
