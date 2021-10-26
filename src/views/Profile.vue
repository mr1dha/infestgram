<template>
<div>
  <Navbar />
  <Banner :data="user"/>
  <PostWrapper>
      <div class="col-md-7" v-for="post in posts" :key="post.id">
        <Post :post="post" :user="user" :nav="true" />
      </div>
  </PostWrapper>
</div>
</template>
 
<script>
import Navbar from "../components/Navbar.vue";
import PostWrapper from "../components/PostWrapper.vue";
import Post from "../components/Post.vue";
import Banner from "../components/Banner.vue";
import axios from "axios";

export default {
  name: "Profile",
  components: { Navbar, PostWrapper, Post, Banner },
  data() {
    return {
      posts: [],
      user: [],
    };
  },
  mounted() {
    axios
      .get("user/posts")
      .then((response) => (this.posts = response.data))
      .catch((err) => console.log(err));
    axios
      .get("user")
      .then((response) => (this.user = response.data))
      .catch((err) => console.log(err.response.data));
  },
};
</script>
