<template>
  <div class="goodsClass">
    <div class="topline line_c"></div>
    <div class="goodsBox">
      <div class="classBox" :key='i' v-for="(x,i) in listData.goodsList">
        <goods-class :goods='x'></goods-class>
        <div class="line line_c"></div>
      </div>
    </div>
  </div>
</template>

<script>
import goodsClass from "@/components/goodsClass";

export default {
  data() {
    return {
      goodsClass: {},
      listData: {
        goodsList: []
      }
    };
  },

  components: {
    goodsClass
  },

  methods: {
    getList() {
      this.goodsClass = wx.getStorageSync("goodsClass");
      var that = this;
      wx.request({
        url:
          "https://easy-mock.com/mock/5b9b68d11615c53f58edfeda/getGoodsClass",
        methods: "get",
        data: {
          url: encodeURIComponent(that.goodsClass.url),
          title: encodeURIComponent(that.goodsClass.title)
        },
        success: res => {
          if (res.data.code == 1) {
            that.upList(res.data.data);
          } else {
            console.log("网络错误!");
          }
        }
      });
    },
    upList(data) {
      this.listData.goodsList = data.arr || [];
      console.log(this.listData)
    }
  },

  created() {},
  onShow() {
    this.getList();
  },
  onHide(){
    this.listData.goodsList=[]
  },
  onLoad: function(option) {
        this.listData.goodsList=[]

    wx.setNavigationBarTitle({
      title: option.title
    });
  }
};
</script>

<style scoped lang="scss">
.goodsClass {
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
  .line{
    height: 1rpx;
    width: 100vw;
  }
}
</style>
