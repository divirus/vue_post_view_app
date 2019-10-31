<template>
  <div class="comment-item">
    <p class="comment-email">@{{comment.email}}</p>
    <p class="comment-name">{{comment.name}}</p>
    <p class="comment-body">{{comment.body}}</p>
  </div>
</template>

<script>
export default {
  name: "PostsComment",
  props: ["comment"],
};
</script>

<style scoped>
p,
a {
  font-size: 14px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.comment-item {
  background: #f4f4f4;
  padding: 15px 10px;
  border-bottom: 1px #ccc dotted;
}

.comment-name {
  font-weight: 600;
}

.comment-email {
  color: #b6b8b6;
}

</style>

