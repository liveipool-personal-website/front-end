<template>
  <div class="about">
    <h1>{{ msg }}</h1>
    <el-button type="primary" @click="goHome">主页</el-button>
    <el-button type="primary" @click="goToBlog">博客</el-button>
    <el-button type="primary" @click="goToLogin">作者登录</el-button>
  </div>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      msg: '关于作者页面',
    };
  },
  methods: {
    goHome() {
      this.$router.push({ name: 'Home' });
    },
    goToBlog() {
      this.$router.push({ name: 'Blog' });
    },
    goToLogin() {
      this.$router.push({ name: 'Login' });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
</style>
