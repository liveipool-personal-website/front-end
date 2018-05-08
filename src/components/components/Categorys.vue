<template>
  <div class="categorys">
    <i class="el-icon-arrow-left"></i>
    <el-row class="categorys-text">
      <el-col
        :class="{ 'active-category': category === currentActiveCategory }"
        :span="span" v-for="category in categorys" :key="category.index">
        <span class="category" @click="handleCategoryClick(category)">{{ category }}</span>
      </el-col>
    </el-row>
    <i class="el-icon-arrow-right"></i>
  </div>
</template>

<script>
export default {
  // 分类列表
  name: 'Categorys',
  props: {
    // 每个数据占多少比例
    span: {
      type: Number,
      default: 6,
    },
    // 显示在页面上的类别数组
    categorys: {
      type: Array,
      default: function defaultCategorys() {
        return [];
      },
    },
    // 博客标题列表部分相关数据
    blog: {
      type: Object,
      default: function defaultBlog() {
        return {
          // 拿到的所有博客信息列表
          allBlogInfos: [],
          // 显示在页面上的博客信息列表
          blogInfos: [],
          // 当前显示的博客的blogId
          currentActiveBlogId: 0,
        };
      },
    },
  },
  data() {
    return {
      currentActiveCategory: '全部',
    };
  },
  methods: {
    handleCategoryClick(category) {
      this.currentActiveCategory = category;
      // 每一次更换类别，需要更改博客信息列表
      // 这里的具体实现还有待进一步设计，现在是只有十个博客信息
      this.blog.blogInfos = [];
      for (let i = 0; i < this.blog.allBlogInfos.length; i += 1) {
        if (this.currentActiveCategory === '全部' || this.blog.allBlogInfos[i].category === this.currentActiveCategory) {
          this.blog.blogInfos.push(this.blog.allBlogInfos[i]);
        }
      }
      // 将列表第一个默认为当前显示博客
      this.blog.currentActiveBlogId = this.blog.blogInfos[0].blogId;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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

.active-category {
  background-color: #FFDDAA;
}
</style>
