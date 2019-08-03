<template>
  <div>
    <Header />
    <nuxt />
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/header";
import Footer from "@/components/footer";
export default {
  components: {
    Header,
    Footer
  }
};
</script>

<style lang="less">
/*
nuxt提供了一个公共布局组件layouts/default.vue layouts公共布局组件默认作用于所有页面
*/
html {
  font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI",
    Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

//内外边距初始化
* {
  margin: 0;
  padding: 0;
}

//ul去除小圆点
ul,
li,
ol {
  list-style: none;
}

a {
  //a标签继承父元素颜色
  color: inherit;
  //a标签去除下划线
  text-decoration: none;
}
//设置字体样式
em,
i {
  font-style: normal;
}
</style>
