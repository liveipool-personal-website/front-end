<template>
  <div class="blog">
    <el-row class="big-content-container hidden-xs-only">
      <el-col
        class="left-content"
        :sm="6" :md="6" :lg="6" :xl="6">
        <el-input
          placeholder="请输入博客名进行搜索"
          prefix-icon="el-icon-search"
          v-model="searchBar">
        </el-input>
        <categorys :categorys="categorys"></categorys>
        <blog-infos :blogInfos="blogInfos" :blogContent="blogContent"></blog-infos>
      </el-col>
      <el-col
        class="right-content"
        @scroll.native="scrollEvent"
        :sm="18" :md="18" :lg="18" :xl="18">
        <normal-head-bar :buttons="buttons"></normal-head-bar>
        <floating-head-bar id="floatingHeadBar" :buttons="buttons"></floating-head-bar>
        <blog-content :blogContent="blogContent"></blog-content>
      </el-col>
    </el-row>

    <div class="small-content-container hidden-sm-and-up">
      <el-input
        class="small-search-bar"
        placeholder="请输入博客名进行搜索"
        prefix-icon="el-icon-search"
        v-model="searchBar">
      </el-input>
      <el-dropdown trigger="click" @command="handleCommand">
        <i class="el-icon-menu"></i>
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item command="Home">主页</el-dropdown-item>
          <el-dropdown-item command="About">关于作者</el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
      <categorys :categorys="categorys"></categorys>
      <blog-infos :blogInfos="blogInfos"></blog-infos>
    </div>
  </div>
</template>

<script>
import constants from '@/utils/constants';
import Categorys from './components/Categorys';
import BlogInfos from './components/BlogInfos';
import NormalHeadBar from './components/NormalHeadBar';
import FloatingHeadBar from './components/FloatingHeadBar';
import BlogContent from './components/BlogContent';

export default {
  name: 'Blog',
  components: {
    Categorys,
    BlogInfos,
    NormalHeadBar,
    FloatingHeadBar,
    BlogContent,
  },
  data() {
    return {
      // 搜索框的输入值
      searchBar: '',

      // 类别组件相关数据
      // 全部类别数组
      allCategorys: [],
      // 显示在页面上的类别数组
      categorys: ['全部'],
      // 当前显示的第一个类别的序号
      firstCategoryNumber: 1,
      // 页面上总共显示多少个类别+1
      showCategorysCount: 3,

      // 博客标题列表部分相关数据
      // 显示在页面上的博客信息列表
      blogInfos: [],
      // 每次请求多少个博客信息
      blogInfosCount: 10,
      // 最近一次请求的博客信息列表的序号
      blogInfosNumber: 0,

      // 普通的处于页面正常结构中的顶部跳转按钮列表中的各按钮信息
      buttons: [
        {
          content: '主页',
          routeName: 'Home',
        },
        {
          content: '关于作者',
          routeName: 'About',
        },
        {
          content: '登录',
          routeName: 'Login',
        },
      ],

      // 跳转按钮列表
      oldScrollTop: 0,

      // 博客内容部分
      blogContent: {
        title: '',
        content: '',
      },
    };
  },
  methods: {
    // 上下滑动博客内容部分的滑动时间
    scrollEvent(event) {
      const floatingHeadBar = document.getElementById('floatingHeadBar');
      if (event.target.scrollTop > this.oldScrollTop || event.target.scrollTop < 58) {
        floatingHeadBar.style.display = 'none';
      } else {
        floatingHeadBar.style.display = '';
      }
      this.oldScrollTop = event.target.scrollTop;
    },
    // 跳转按钮下拉菜单的监听事件
    handleCommand(command) {
      this.$router.push({ name: command });
    },
    // 将一个对象数组里的各项按时间由近到远排序
    sortObjectArrayWithDate(arr) {
      const resultArr = arr;
      resultArr.sort((obj1, obj2) => obj1.uploadDate < obj2.uploadDate);
      return resultArr;
    },
  },
  mounted() {
    // 获取类别数组
    this.$http.get(`${constants.serverUrl}/blog/categorys`)
      .then((response) => {
        const tmpData = response.body;
        for (let i = this.firstCategoryNumber - 1; i < this.showCategorysCount; i += 1) {
          this.categorys.push(tmpData[i].category);
        }
      });

    // 获取类别“全部”下的初始各博客信息
    this.$http.get(`${constants.serverUrl}/blog/blogInfos/${this.blogInfosNumber}/${this.blogInfosCount}`)
      .then((response) => {
        // 将拿到的各博客信息数据按照时间排序
        // 但其实这个工作应该后端做，并且以后每次新添加的博客的上传日期都应该更新
        const tmpData = this.sortObjectArrayWithDate(response.body);
        for (let i = 0; i < tmpData.length; i += 1) {
          this.blogInfos.push(tmpData[i]);
        }

        // 获取默认的博客信息列表的第一篇博客的内容
        this.$http.get(`${constants.serverUrl}/blog/${this.blogInfos[0].blogId}`)
          .then((res) => {
            this.blogContent.title = res.body.title;
            this.blogContent.content = res.body.content;
          });
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.blog {
  width: 100%;
  height: 100vh;
}

.big-content-container {
  width: 100%;
  height: 100%;
}

.left-content {
  height: 100%;
  background-color: #fef4eb;
}

.right-content {
  height: 100%;
  overflow-y: auto;
}

.small-content-container {
  width: 100%;
  height: 100%;
  background-color: #fef4eb;
}

.small-search-bar {
  width: calc(100% - 40px);
}
</style>

<style>
.blog .big-content-container .left-content .el-input__inner,
.blog .small-content-container .el-input__inner {
  border: 0;
  background-color: #fef4eb;
  color: #3c3c3c;
}

.blog .small-content-container .el-dropdown {
  position: absolute;
  top: 0;
  right: 0;
  width: 40px;
  height: 40px;
}
.blog .small-content-container .el-dropdown .el-icon-menu {
  display: inline-block;
  margin: 5px;
  cursor: pointer;
  font-size: 30px
}
</style>
