<template>
  <div id="app">
    <Posts v-bind:posts="posts" />
    <PostsDetails ref="PostsDetails"/>
  </div>
</template>

<script>
import Posts from '../components/Posts';
import PostsDetails from '../components/PostsDetails';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Posts,
    PostsDetails
  },
  data() {
    return {
      posts: [],
      postsData: [],
      usersData: []
    }
  },
  async created() {
    await axios.get('https://jsonplaceholder.typicode.com/posts')
      .then(res => this.postsData = res.data)
      .catch(err => console.log(err));
    await axios.get('https://jsonplaceholder.typicode.com/users')
      .then(res => this.usersData = res.data)
      .catch(err => console.log(err));

    this.postsData.forEach((post) => {
      let user = this.usersData.find(user => user.id === post.userId);
      let postObj = {
          'id': post.id, 
          'title': post.title, 
          'body': post.body, 
          'postpreview': post.body.slice(0, 50),
          'name': user ? user.name : null,
          'username': user ? user.username : null
      };

      this.posts.push(postObj);
    }, this);
  }

}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
