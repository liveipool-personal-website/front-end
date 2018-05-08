<template>
  <div class="blog-infos">
    <div
      v-for="blogInfo in blog.blogInfos"
      :key="blogInfo.index"
      :class="blogInfo.blogId === blog.currentActiveBlogId ? 'blog-info active-blog' : 'blog-info'"
      @click="handleBlogClick(blogInfo.blogId)">
      <div class="blog-title">· {{ blogInfo.title }}</div>
      <div class="blog-upload-date">{{ blogInfo.uploadDate }}</div>
    </div>
  </div>
</template>

<script>
export default {
  // 博客相关信息
  name: 'BlogInfos',
  props: {
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
  methods: {
    handleBlogClick(blogId) {
      this.blog.currentActiveBlogId = blogId;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.blog-infos {
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

.active-blog {
  background-color: #FFDDAA;
}
</style>
