<template>
  <div>
    <Navbar />
    <PostWrapper>
      <div class="col-md-7" v-for="post in posts" :key="post.id">
        <Post :post="post" :user="post.user" :nav="false" />
      </div>
    </PostWrapper>
  </div>
</template>

<script>
import axios from "axios";
import Navbar from "@/components/Navbar.vue";
import Post from "@/components/Post.vue";
import PostWrapper from "@/components/PostWrapper.vue";

export default {
  name: "Home",
  components: { Navbar, Post, PostWrapper },
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    axios
      .get("posts")
      .then((res) => (this.posts = res.data))
      .catch((err) => console.log(err));
  },
};
</script>
