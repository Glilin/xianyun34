<template>
  <div class="header">
    <div class="main">
      <el-row type="flex" justify="space-between">
        <!--logo 图片  -->
        <div class="logo">
          <img src="http://157.122.54.189:9093/images/logo.jpg" alt />
        </div>
        <!-- 菜单menu -->
        <el-row type="flex" class="nanvs">
          <nuxt-link to="/">首页</nuxt-link>
          <nuxt-link to="/post">旅游攻略</nuxt-link>
          <nuxt-link to="/hotel">酒店</nuxt-link>
          <nuxt-link to="/air">国内机票</nuxt-link>
        </el-row>
        <!-- 登入注册 -->
        <div v-if="false">
          <nuxt-link to="/user/login">登入注册</nuxt-link>
        </div>
        <!-- 登入之后的布局    dropdown 下拉菜单   dropdown 下拉菜单 dropdown-->
        <div v-else>
          <el-dropdown>
            <span class="el-dropdown-link">
              <img src="http://157.122.54.189:9095/assets/images/avatar.jpg" alt />
              银河抽水机
              <i class="el-icon-arrow-down el-icon--right"></i>
            </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item>个人中心</el-dropdown-item>
              <el-dropdown-item>退出</el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
        </div>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="less" scoped>
.main {
  width: 1000px;
  margin: 0 auto;
}
.header {
  height: 60px;
  line-height: 60px;
  border-bottom: 1px solid #ccc;
  box-shadow: 0 3px 3px #eee;
}
.logo {
  margin-top: 9px;
  img {
    width: 156px;
    height: 43px;
    display: block;
  }
}
.nanvs {
  flex: 1;
  margin-left: 20px;
  a {
    display: block;
    padding: 0 20px;
    height: 60px;
    line-height: 60px;
    box-sizing: border-box;
    &:hover {
      color: #4093ff;
      border-bottom: 5px solid #409eff;
    }
  }
  .nuxt-link-exact-active {
    background: #409eff;
    color: #fff;
    &:hover {
      color: #fff;
    }
  }
}
.el-dropdown-link {
  img {
    width: 36px;
    height: 36px;
    vertical-align: middle;
    border-radius: 50%;
  }
}
/*
expected 预期

flex-grow属性定义项目的放大比例，值默认为0，如果有等分剩余空间，比例也不放大，
值为1时，如果有等分剩余空间，比例放大
flex-shrink属性定义项目的缩小比例 值默认为1，空间不足时，等比例缩小， 如果有一个值为o
其他为默认值1  ,则默认值1 缩小 负值对属性无效
*/
</style>