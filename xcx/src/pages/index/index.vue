<!--
 * @Description: 
 * @Author: 靳小健
 * @Email: jinxiaojian@youxin.com
 * @LastEditors: 靳小健
 * @Date: 2019-03-12 14:50:18
 * @LastEditTime: 2019-03-12 14:51:27
 -->
<template>
  <div class="index">
    <div class="topline line_c"></div>
    <aside-nav :activityNum='activityNum' @choiceList='choiceList'></aside-nav>
    <div class="mainBox">
      <swiper v-if="listData.imgUrls.length>0" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration" :circular='circular'>
        <block :key='i' v-for="(x,i) in listData.imgUrls">
          <swiper-item>
            <image :src="x" class="slide-image" />
          </swiper-item>
        </block>
      </swiper>
      <div v-if="listData.goodsList.length>0">
        <h3 class="theme_c">{{listData.goodsListTitle}}</h3>
        <div class="goodsbox">
          <div class="goods" :key='i' v-for="(x,i) in listData.goodsList">
            <goods :goods='x'></goods>
          </div>
        </div>
      </div>
      <div v-if="listData.goodsList2.length>0">
        <h3 class="theme_c">{{listData.goodsListTitle2}}</h3>
        <div class="goodsbox">
          <div class="goods" :key='i' v-for="(x,i) in listData.goodsList2">
            <goods :goods='x'></goods>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import asideNav from "@/components/asideNav";
import goods from "@/components/goods";

export default {
  data() {
    return {
      activityNum: 0,
      listData: {
        goodsListTitle: "",
        goodsList: [],
        goodsListTitle2: "",
        goodsList2: [],
        imgUrls: []
      },

      indicatorDots: false,
      autoplay: true,
      interval: 5000,
      duration: 1000,
      circular: true
    };
  },

  components: {
    asideNav,
    goods
  },

  methods: {
    choiceList(i) {
      this.activityNum = i;
      this.getList();
    },
    getList() {
      this.listData = {
        goodsListTitle: "",
        goodsList: [],
        goodsListTitle2: "",
        goodsList2: [],
        imgUrls: []
      };
      var that = this;
      wx.request({
        url: "https://easy-mock.com/mock/5b9b68d11615c53f58edfeda/getList",
        methods: "get",
        data: {
          activityNum: this.activityNum
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
      if (data.req != this.activityNum) {
        return;
      }
      this.listData.goodsListTitle = data.goodsListTitle || "标题";
      this.listData.goodsListTitle2 = data.goodsListTitle2 || "标题";
      this.listData.imgUrls = data.imgUrls || [];
      this.listData.goodsList = data.goodsList || [];
      this.listData.goodsList2 = data.goodsList2 || [];
    }
  },

  created() {},
  onShow() {
    this.getList();
  },
  onLoad() {
    wx.setNavigationBarTitle({
      title: "jxjweb.top商城"
    });
  }
};
</script>

<style scoped lang="scss">
.index {
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

  h3 {
    padding-top: 20rpx;
    line-height: 50rpx;
    font-size: 30rpx;
    text-indent: 30rpx;
  }

  .goodsbox {
    padding: 10rpx;
    overflow: hidden;

    .goods {
      width: 150rpx;
      overflow: hidden;
      float: left;
      margin-left: 15rpx;
    }
  }

  .mainBox {
    min-height: 100vh;
    padding-left: 30vw;
    background: #fff;
  }

  swiper {
    width: 100%;
    height: 300rpx;

    image {
      width: 100%;
      height: 100%;
    }
  }
}
</style>
