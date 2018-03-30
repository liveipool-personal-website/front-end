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
        <div class="blogs-info">
          <div class="blog-info" v-for="blogInfo in blogsInfo" :key="blogInfo in blogsInfo">
            <div class="blog-title">· {{ blogInfo.title }}</div>
            <div class="blog-upload-date">{{ blogInfo.uploadDate }}</div>
          </div>
        </div>
      </el-col>
      <el-col class="right-content" :sm="18" :md="18" :lg="18" :xl="18">
        <div>右</div>
      </el-col>
    </el-row>
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

      // 文章标题列表部分相关数据
      // 所有现在已存的文章信息，模拟后端数据
      allBlogsInfo: [],
      // 显示在页面上的文章信息列表
      blogsInfo: [],
      // 每次请求多少个文章信息
      blogsInfoCount: 15,
      // 最近一次请求的文章信息列表的序号
      blogsInfoNumber: 0,
    };
  },
  methods: {
  },
  mounted() {
    // 获取类别种类
    const allCategorys = ['全部', '数学', '美术', '英语', '体育', '语文', '政治'];
    for (let i = this.firstCategoryNumber; i < this.showCategorysCount; i += 1) {
      this.categorys.push(allCategorys[i]);
    }

    // 获取所有现在已存的文章信息列表，模拟后端数据
    const allBlogsInfo = [
      {
        title: '如何评价中山大学',
        uploadDate: '2018.03.28',
      }, {
        title: '春游',
        uploadDate: '2018.03.27',
      }, {
        title: '星巴克焦糖咖啡星冰乐',
        uploadDate: '2018.03.26',
      }, {
        title: '我是一个特别长特别长特别长特别长特别长的名字',
        uploadDate: '2018.03.25',
      }, {
        title: '今天天气如何',
        uploadDate: '2018.03.24',
      }, {
        title: '毕业设计',
        uploadDate: '2018.03.23',
      }, {
        title: '软件工程专业',
        uploadDate: '2018.03.22',
      }, {
        title: '政治',
        uploadDate: '2018.03.21',
      }, {
        title: 'iphoneX',
        uploadDate: '2018.03.21',
      }, {
        title: '猫',
        uploadDate: '2018.03.20',
      }, {
        title: '橘猫',
        uploadDate: '2018.03.19',
      },
    ];
    this.allBlogsInfo = allBlogsInfo;
    // 获取当前种类下的各文章信息
    for (let i = this.blogsInfoNumber;
      i < this.blogsInfoCount * (this.blogsInfoNumber + 1); i += 1) {
      if (this.allBlogsInfo[i]) {
        this.blogsInfo.push(this.allBlogsInfo[i]);
      }
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
  top: 9px;
  margin: 0 21px;
  width: calc(100% - 42px);
  display: inline-block;

}

.categorys-text .el-col {
  text-align: center;
  cursor: pointer;
}

.blogs-info {
  width: 100%;
  height: calc(100% - 80px);
  overflow-y: auto;
}

.blog-info {
  width: 100%;
  height: 40px;
  margin-top: 10px;
  margin-bottom: 10px;
  cursor: pointer;
}

.blog-info:hover {
  background-color: #FFDDAA;
}

.blog-title {
  width: calc(100% - 25px);
  height: 22px;
  padding: 0 10px 0 15px;
  font-size: 18px;
  color: #3c3c3c;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.blog-upload-date {
  width: calc(100% - 39px);
  height: 18px;
  padding: 0 10px 0 29px;
  font-size: 14px;
  color: #aaa;
}
</style>

<style>
.blog .content-container .left-content .el-input__inner {
  border: 0;
  background-color: #fef4eb;
  color: #3c3c3c;
}
</style>
