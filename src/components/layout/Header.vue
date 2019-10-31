<template>
  <header class="header">
    <h1>Daily bunch of posts</h1>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
}
</script>

<style scoped>
  h1 {
    font-weight: 900;
  }

  .header {
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px;
  }

  .header a {
    color: #fff;
    padding-right: 5px;
    text-decoration: none;
  }
</style>


