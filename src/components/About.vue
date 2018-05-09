<template>
  <div class="about">
    <h1>{{ msg }}</h1>
    <el-button type="primary" @click="goHome">主页</el-button>
    <el-button type="primary" @click="goToBlog">博客</el-button>
    <el-button type="primary" @click="goToLogin">作者登录</el-button>
    <div v-for="info in infos" :key="info.key">
      <div> {{info.key}} : {{info.value}}</div>
    </div>
  </div>
</template>

<script>
import constants from '@/utils/constants';

export default {
  name: 'About',
  data() {
    return {
      msg: '关于作者页面',
      // 个人信息条目
      infos: [],
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
  mounted() {
    // 获取个人信息接口
    this.$http.get(`${constants.serverUrl}/about/personalInfo`)
      .then((response) => {
        // 拿到个人信息条目数组
        const tmpArr = Object.keys(response.body[0]);
        for (let i = 0; i < tmpArr.length; i += 1) {
          const tmpObject = {};
          tmpObject.key = tmpArr[i];
          tmpObject.value = response.body[0][tmpArr[i]];
          this.infos.push(tmpObject);
        }
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.about {
  width: 600px;
  margin: 0 auto;
  text-align: center;
}

h1, h2 {
  font-weight: normal;
}
</style>
