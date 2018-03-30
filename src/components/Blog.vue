<template>
  <div class="blog">
    <el-row class="content-container">
      <el-col class="left-content" :sm="6" :md="6" :lg="6" :xl="6">
        <el-input
          class="search-bar"
          placeholder="请输入内容"
          prefix-icon="el-icon-search"
          v-model="searchBar">
        </el-input>
        <el-pagination
          class="category"
          layout="prev, pager, next"
          :total="10">
        </el-pagination>
        <div class="blog-titles">文章标题</div>
      </el-col>
      <el-col class="right-content" :sm="18" :md="18" :lg="18" :xl="18">
        <div>右</div>
      </el-col>
    </el-row>
<!--     <h1>{{ msg }}</h1>
    <el-button type="primary" @click="goHome">主页</el-button>
    <el-button type="primary" @click="goToAbout">关于作者</el-button>
    <el-button type="primary" @click="goToLogin">作者登录</el-button> -->
  </div>
</template>

<script>
export default {
  name: 'Blog',
  data() {
    return {
      // msg: '博客页面',
      searchBar: '',
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
  border: 2px solid #58a;
}

.right-content {
  height: 100%;
  border: 2px solid #fb3;
}

.search-bar {

}

.category {

}

.blog-titles {
  background-color: #39f;
}
</style>
