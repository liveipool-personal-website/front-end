<template>
  <div class="home">
    <h1>{{ msg }}</h1>
    <h2>主页</h2>
    <el-button type="primary" @click="goToBlog">博客</el-button>
    <el-button type="primary" @click="goToAbout">关于作者</el-button>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data() {
    return {
      msg: 'Personal website of Liveipool',
    };
  },
  methods: {
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
h1, h2 {
  font-weight: normal;
}
</style>
