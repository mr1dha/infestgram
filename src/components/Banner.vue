<template>
  <div class="banner">
    <div class="cover-image shadow-sm"></div>
    <div class="profile-image shadow" :style="{backgroundImage: `url('${data.profile}')`}"></div>
    <div class="profile-info text-center mt-2">
      <h4 class="name fw-bold">{{data.name}}</h4>
      <span class="text-muted">{{data.email}}</span>
    </div>
  </div>
</template>
 
<script>
export default {
  name: "Banner",
  props: ["data"],
};
</script>
 
<style>
.banner {
  margin-top: 74.8px;
}

.banner .cover-image,
.banner .profile-image {
  background-size: cover !important;
  background-position: center !important;
  background-repeat: no-repeat !important;
}

.banner .cover-image {
  height: 350px;
  background: salmon;
  background-image: url(../assets/cover.jpg);
}

.banner .profile-image {
  width: 225px;
  height: 225px;
  border-radius: 50%;
  border: 8px solid white;
  margin: -115px auto 0 auto;
  background-color: white;
}
</style>
