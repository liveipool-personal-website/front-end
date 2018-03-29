<template>
  <div class="login">
    <h1>{{ msg }}</h1>
    <el-button type="primary" @click="goHome">主页</el-button>
    <el-button type="primary" @click="goToBlog">文章</el-button>
    <el-button type="primary" @click="goToAbout">关于作者</el-button>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
    return {
      msg: '作者登录页面',
    };
  },
  methods: {
    goHome() {
      this.$router.push({ name: 'Home' });
    },
    goToBlog() {
      this.$router.push({ name: 'Blog' });
    },
    goToAbout() {
      this.$router.push({ name: 'About' });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
