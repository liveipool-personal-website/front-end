<template>
  <div class="blog-infos">
    <div
      class="blog-info" v-for="blogInfo in blogInfos"
      :key="blogInfo.index" @click="handleBlogClick(blogInfo)">
      <div class="blog-title">· {{ blogInfo.title }}</div>
      <div class="blog-upload-date">{{ blogInfo.uploadDate }}</div>
    </div>
  </div>
</template>

<script>
import constants from '@/utils/constants';

export default {
  // 博客相关信息
  name: 'BlogInfos',
  props: {
    // 显示在页面上的博客信息列表
    blogInfos: {
      type: Array,
      default: function defaultBlogInfos() {
        return [];
      },
    },
    // 博客内容部分
    blogContent: {
      type: Object,
      default: function defaultBlogContent() {
        return {
          title: '暂无标题',
          content: '暂无内容',
        };
      },
    },
  },
  methods: {
    handleBlogClick(blogInfo) {
      // 获取某篇博客的信息
      this.$http.get(`${constants.serverUrl}/blog/${blogInfo.blogId}`)
        .then((response) => {
          this.blogContent.title = response.body.title;
          this.blogContent.content = response.body.content;
        });
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
</style>
