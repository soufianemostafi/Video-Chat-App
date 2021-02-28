<template>
  <div class="mt-3">
    <div class="text-center text-light" v-if="user">
      Welcome back
      <span class="font-weight-bold text-danger">{{ user.displayName }}</span>
    </div>
    <div class="container text-center">
      <div class="row justify-content-center">
        <div class="col-10 col-md-10 col-lg-8 col-xl-7">
          <h4 class="display-4 text-danger mb-2">Video Chat</h4>
          <p class="lead text-light">
            This app uses Firebase for real time communication and WebRTC to
            create video chats between multiple users, and it's part of my
            school project. -Soufiane MOSTAFI
          </p>
          <router-link
            class="btn btn-outline-danger mr-2"
            to="/login"
            v-if="!user"
            >Log In</router-link
          >
          <router-link
            class="btn btn-outline-danger mr-2"
            to="/register"
            v-if="!user"
            >Register</router-link
          >
          <router-link
            class="btn btn-outline-danger mr-2"
            to="/rooms"
            v-if="user"
            >Rooms</router-link
          >
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Home",
  props: ["user"],
};
</script>
<style type="text/css">
body {
  background: #5b5b5b !important;
}
</style>