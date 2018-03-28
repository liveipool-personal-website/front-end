<template>
  <div class="blog">
    <h1>{{ msg }}</h1>
    <el-button type="primary" @click="goHome">主页</el-button>
    <el-button type="primary" @click="goToAbout">关于作者</el-button>
  </div>
</template>

<script>
export default {
  name: 'Blog',
  data() {
    return {
      msg: '博客页面',
    };
  },
  methods: {
    goHome() {
      this.$router.push({ name: 'Home' });
    },
    goToAbout() {
      this.$router.push({ name: 'About' });
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
