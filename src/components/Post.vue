<template>
    <div v-if="nav" class="post-nav mb-2 text-center">
      <button @click="deletePost()" class="btn btn-outline-danger me-2">
        <i class="bi bi-trash"></i> Hapus
      </button>
      <router-link :to="`/posts/${post.id}/edit`" class="btn btn-outline-primary">
        <i class="bi bi-pencil-fill"></i> Edit
      </router-link>
    </div>
    
    <div class="card card-post shadow">
        <img :src="post.image" class="card-img-top">
        <div class="card-body">
            <p class="mb-2 profile">
            <img :src="user.profile">
            <a href="#"><b>{{ user.name }}</b></a>
            <small class="text-muted float-end">{{ timeUpload }}</small>
            </p>
            <small class="card-text post-caption"> {{ post.caption }}</small>
        </div>
    </div>
</template>

<script>
import moment from "moment";
import axios from "axios";

export default {
  name: "Post",
  props: ["post", "user", "nav"],
  computed: {
    timeUpload() {
      return moment(this.post.created_at).fromNow();
    },
  },
  methods: {
    deletePost() {
      axios
        .delete("/posts/" + this.post.id)
        .then((res) => this.$router.go())
        .catch((err) => console.log(err));
    },
  },
};
</script>
 
<style>
.card-post {
  width: 100%;
  margin-bottom: 2em;
  border-radius: 15px;
}

.card-post .card-body {
  padding: 0 1em 1em;
}

.card-post .card-img-top {
  padding: 0.8em;
}

.card-post .profile img {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  vertical-align: text-top;
  margin-right: 5px;
}

.card-post .profile a {
  text-decoration: none;
  color: unset;
}
</style>
