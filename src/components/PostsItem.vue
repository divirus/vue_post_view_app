<template>
  <div class="posts-item">
    <p class="posts-name line">{{posts.name}}</p>
    <p class="posts-username line">@{{posts.username}}</p>
    <p class="posts-title">{{posts.title}}</p>
    <p class="posts-preview">{{posts.postpreview}}</p>
    <a class="posts-read_more-button" @click="showDetailedPostData(posts)">...read more</a>
  </div>
</template>

<script>
export default {
  name: "PostsItem",
  props: ["posts"],
  methods: {
    showDetailedPostData: function (post) {
      this.$parent.$parent.$refs.PostsDetails.show();
      this.$parent.$parent.$refs.PostsDetails.getPostData(post);
      this.$parent.$parent.$refs.PostsDetails.getPostComments(post.id);
    }
  }
};
</script>

<style scoped>
p,
a {
  font-size: 14px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.posts-item {
  background: #f4f4f4;
  padding: 15px 10px;
  border-bottom: 1px #ccc dotted;
}

.posts-name {
  font-weight: 600;
}

.posts-username {
  color: #b6b8b6;
}

.line {
  display: inline-flex;
  margin-bottom: 5px;
}

.posts-title {
  font-weight: 600;
}

.posts-preview {
  display: inline-flex;
}

.posts-read_more-button {
  color: #3490dc;
  cursor: pointer;
}
</style>

