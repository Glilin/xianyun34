<template>
  <div class="container">
    <!-- 轮播图 使用el-carousel 和 el-carousel-item标签就可以得到一个轮播图-->
    <el-carousel :interval="5000" arrow="always">
      <el-carousel-item v-for="(item,index ) in banners" :key="index">
        <div
          class="banner-image"
          :style="`background:url(${ $axios.defaults.baseURL + item.url}) center center no-repeat; background-size:contain contain`"
        ></div>
      </el-carousel-item>
    </el-carousel>

    <!-- 搜索框 -->
    <div class="banner-content">
      <div class="search-bar">
        <!-- tab栏  -row水平方向，起点在左边-->
        <el-row type="flex" class="search-tab">
          <span
            v-for="(item,index) in options "
            :key="index"
            :class="{active:current==index}"
            @click=" handleClick(index) "
          >
            <i>{{item.title}}</i>
            <!-- <i>攻略</i> -->
          </span>
        </el-row>

        <!-- 输入框 -->
        <el-row type="flex" align="middle" class="search-input">
          <input :placeholder="placeholder " />
          <i class="el-icon-search"></i>
        </el-row>
      </div>
    </div>
  </div>

</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      banners: [],
      options: [
        { title: "攻略", placeholder: "请输入城市" },
        { title: "酒店", placeholder: "请搜索酒店" },
        { title: "机票", placeholder: "" }
      ],
      // 记录当前状态下标
      current: 0,
      placeholder:'请输入城市'
    };
  },
  methods: {
    //把index的值赋值给current
    handleClick(index) {
      console.log(index)
      // 点击机票
      if (index === 2) {
        this.$router.push("/air");
      }
      this.placeholder = this.options[index].placeholder
      this.current = index;
    }
  },
  // 生命周期函数
  mounted() {
    //$开头的属性是vue实列对象的约定用法
    this.$axios({
      url: "/scenics/banners"
    }).then(res => {
      // data是一个数组
      const { data } = res.data;
      this.banners = data;
    });
  }
};
</script>

<style lang="less" scoped>
.container {
  min-width: 1000px;
  margin: 0 auto;
  position: relative;

  /deep/ .el-carousel__container {
    height: 700px;
  }

  .banner-image {
    width: 100%;
    height: 100%;
  }

  .banner-content {
    z-index: 9;
    width: 1000px;
    position: absolute;
    left: 50%;
    top: 45%;
    margin-left: -500px;
    border-top: 1px transparent solid;

    .search-bar {
      width: 552px;
      margin: 0 auto;
    }

    .search-tab {
      .active {
        i {
          color: #333;
        }
        &::after {
          background: #eee;
        }
      }

      span {
        width: 82px;
        height: 36px;
        display: block;
        position: relative;
        margin-right: 8px;
        cursor: pointer;

        i {
          position: absolute;
          z-index: 2;
          display: block;
          width: 100%;
          height: 100%;
          line-height: 30px;
          text-align: center;
          color: #fff;
        }

        &:after {
          position: absolute;
          left: 0;
          top: 0;
          display: block;
          content: "";
          width: 100%;
          height: 100%;
          border: 1px rgba(255, 255, 255, 0.2) solid;
          border-bottom: none;
          transform: scale(1.1, 1.3) perspective(0.7em) rotateX(2.2deg);
          transform-origin: bottom left;
          background: rgba(0, 0, 0, 0.5);
          border-radius: 1px 2px 0 0;
          box-sizing: border-box;
        }
      }
    }

    .search-input {
      width: 550px;
      height: 46px;
      background: #fff;
      border-radius: 0 4px 4px 4px;
      border: 1px rgba(255, 255, 255, 0.2) solid;
      border-top: none;
      box-sizing: unset;

      input {
        flex: 1;
        height: 20px;
        padding: 13px 15px;
        outline: none;
        border: 0;
        font-size: 16px;
      }

      .el-icon-search {
        cursor: pointer;
        font-size: 22px;
        padding: 0 10px;
        font-weight: bold;
      }
    }
  }
}
</style>