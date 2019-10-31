<template>
  <div>
    <div v-bind:key="posts.id" v-for="posts in posts">
      <PostsItem v-bind:posts="posts" />
    </div>
  </div>
</template>

<script>
import PostsItem from './PostsItem.vue';

export default {
  name: "Posts",
  components: {
    PostsItem
  },
  props: ["posts"]
}
</script>

<style scoped>

</style>

