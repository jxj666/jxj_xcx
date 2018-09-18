<script>
export default {
  created() {
    // 调用API从本地缓存中获取数据
    const logs = wx.getStorageSync("logs") || [];
    logs.unshift(Date.now());
    wx.setStorageSync("logs", logs);

    console.log("app created and cache logs by setStorageSync");
  }
};
</script>

<style>
.container {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding: 200rpx 0;
  box-sizing: border-box;
}
/* this rule will be remove */
* {
  transition: width 2s;
  -moz-transition: width 2s;
  -webkit-transition: width 2s;
  -o-transition: width 2s;
}
.theme_c {
  color: #ff142d;
}
.first_c {
  color: #2e2e33;
}
.second_c {
  color: #919199;
}
.third_c {
  color: #d7d7d9;
}
.line_c {
  background: #ededf0;
}
.bg_c {
  background: #f7f7fa;
}
.theme_bg_c {
  background: #ff142d;
}
.fff_bg_c{
  background: #fff;
}
</style>
