<template>
  <div v-if="showModal" class="modal-mask">
    <div class="modal-wrapper">
      <div class="modal-container">
        <div class="modal-header">
          <p class="modal-name">{{post.name}}</p>
          <p class="modal-username">@{{post.username}}</p>
        </div>

        <p class="modal-close-button" @click="close">x</p>

        <div class="modal-title">
          <slot name="title">{{post.title}}</slot>
        </div>

        <div class="modal-body">
          <slot name="body">{{post.body}}</slot>
        </div>

        <div class="modal-comments-section">
          <div class="modal-comment" v-bind:key="comment.id" v-for="comment in comments">
            <PostsComment v-bind:comment="comment" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import PostsComment from '../components/PostsComment';

export default {
  name: "PostsDetails",
  components: {
    PostsComment
  },
  data() {
    return {
      showModal: false,
      post: {
        username: null,
        name: null,
        title: null,
        body: null
      },
      comments: []
    };
  },
  methods: {
    show: function() {
      this.showModal = true;
    },
    close: function() {
      this.showModal = false;
    },
    getPostData: function(postData) {
      this.post.username = postData.username;
      this.post.name = postData.name;
      this.post.title = postData.title;
      this.post.body = postData.body;
    },
    getPostComments: function(id) {
      axios.get(`https://jsonplaceholder.typicode.com/comments?postId=${id}`)
      .then(res => this.comments = res.data)
      .catch(err => console.log(err));
    }
  }
};
</script>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 550px;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #fff;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  font-family: Helvetica, Arial, sans-serif;
}

.modal-header {
  margin: 10px 0;
  display: inline-flex;
}

.modal-name {
  font-weight: 300;
}

.modal-username {
  color: #b6b8b6;
}

.modal-title {
  font-weight: 600;
}

.modal-body {
  margin: 10px 0;
}

.modal-close-button {
  float: right;
  margin: -10px;
  color: #b6b8b6;
  cursor: pointer;
  font-size: 17px;
}

.modal-comments-section {
  max-height: 250px;
  overflow: auto;
}
</style>