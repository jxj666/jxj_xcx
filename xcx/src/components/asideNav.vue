<template>
  <div class="asideNav">
<div class="listbox">
  <div class="list first_c" v-for="(x,i) in list" :class="{activity:i==activityNum}" @click='choiceList(i)'>
    {{x}}
  </div>
</div>
  </div>
</template>

<script>
export default {
  props: ['activityNum'],
  data() {
    return {
      list: ["免息推荐", "手机", "电脑办公", "数码", "美妆护肤", "运动户外"]
    };
  },
  methods:{
    choiceList(i){
      // this.activityNum=i;
      this.$emit('choiceList',i)
    }
  }
};
</script>

<style scoped lang='scss'>
.asideNav {
  width: 30vw;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background: #fff;
  border-right: 1rpx solid #EDEDF0;
  .listbox {
    padding: 20 px 0;
    .list {
      font-size: 30rpx;
      margin: 10rpx 0;
      line-height: 50rpx;
      text-align: center;
    }
    .activity {
      color: #ff142d;
      border-left: 5rpx solid #ff142d;
    }
  }
}
</style>
