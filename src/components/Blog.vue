<template>
  <div class="blog">
    <el-row class="content-container">
      <el-col class="left-content" :sm="6" :md="6" :lg="6" :xl="6">
        <el-input
          class="search-bar"
          placeholder="请输入文章名进行搜索"
          prefix-icon="el-icon-search"
          v-model="searchBar">
        </el-input>
        <div class="categorys">
          <i class="el-icon-arrow-left"></i>
          <el-row class="categorys-text">
            <el-col :span="6" v-for="category in categorys" :key="category">
              <span class="category">{{ category }}</span>
            </el-col>
          </el-row>
          <i class="el-icon-arrow-right"></i>
        </div>
        <div class="blog-titles">文章标题</div>
      </el-col>
      <el-col class="right-content" :sm="18" :md="18" :lg="18" :xl="18">
        <div>右</div>
      </el-col>
    </el-row>
    <!-- <el-button type="primary" @click="goHome">主页</el-button> -->
    <!-- <el-button type="primary" @click="goToAbout">关于作者</el-button> -->
    <!-- <el-button type="primary" @click="goToLogin">作者登录</el-button> -->
  </div>
</template>

<script>
export default {
  name: 'Blog',
  data() {
    return {
      // 搜索框的输入值
      searchBar: '',

      // 类别部分相关数据
      // 全部类别数组
      allCategorys: [],
      // 显示在页面上的类别
      categorys: [],
      // 当前显示的第一个类别的序号
      firstCategoryNumber: 0,
      // 页面上总共显示多少个类别
      showCategorysCount: 4,
    };
  },
  methods: {
    // goHome() {
    //   this.$router.push({ name: 'Home' });
    // },
    // goToAbout() {
    //   this.$router.push({ name: 'About' });
    // },
    // goToLogin() {
    //   this.$router.push({ name: 'Login' });
    // },
  },
  mounted() {
    const allCategorys = ['全部', '数学', '美术', '英语', '体育', '语文', '政治'];
    for (let i = this.firstCategoryNumber; i < this.showCategorysCount; i += 1) {
      this.categorys.push(allCategorys[i]);
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/*h1, h2 {
  font-weight: normal;
}*/
.blog {
  width: 100%;
  height: 100vh;
}

.content-container {
  width: 100%;
  height: 100%;
}

.left-content {
  height: 100%;
  background-color: #fef4eb;
}

.right-content {
  height: 100%;
  border: 2px solid #fb3;
}

.search-bar {

}

.categorys {
  position: relative;
  width: 100%;
  height: 40px;
  border: 0;
}

.el-icon-arrow-left,
.el-icon-arrow-right {
  position: absolute;
  width: 16px;
  height: 16px;
  top: 12px;
}

.el-icon-arrow-left {
  left: 5px;
}

.el-icon-arrow-right {
  right: 5px;
}

.categorys-text {
  position: relative;
  top: 8px;
  margin: 0 21px;
  width: calc(100% - 42px);
  display: inline-block;
}

.categorys-text .el-col {
  text-align: center;
}

.blog-titles {
  background-color: #39f;
}
</style>

<style>
.blog .content-container .left-content .el-input__inner {
  border: 0;
  background-color: #fef4eb;
}
</style>
