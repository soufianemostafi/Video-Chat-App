<template>
  <div class="container mt-4">
    <div class="row justify-content-center">
      <div class="col-12 col-md-9 col-lg-7">
        <h1 class="font-weight-light text-center text-light"> Add a Room </h1>

        <div class="card bg-light">
          <div class="card-body text-center">
            <form class="formgroup">
              <div class="input-group input-group-lg">
                <input
                  type="text"
                  class="form-control"
                  name="roomName"
                  placeholder="Room name"
                  aria-describedby="buttonAdd"
                  v-model="roomName"
                  ref="roomName"
                />
                <div class="input-group-append">
                  <button
                    type="submit"
                    class="btn btn-sm btn-info btn-danger"
                    id="buttonAdd"
                    @click.prevent="handleAdd"
                  >
                    +
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-11 col-md-8 col-lg-6">
        <div class="card border-top-0 rounded-0">
          <div class="card-body py-2">
            <h4 class="card-title m-0 text-center font-italic text-danger">Your Rooms</h4>
          </div>
          <div class="list-group list-group-flush">
            <div
              class="list-group-item d-flex"
              v-for="item in rooms"
              :key="item.id"
            >
              <section
                class="btn-group align-self-center font-italic"
                role="group"
                aria-label="Room Options"
              >
                <section
                  class="btn-group align-self-center"
                  role="group"
                  aria-label="Room Options"
                >
                  <button
                    class="btn btn-sm btn-outline-secondary"
                    title="Delete Room"
                    @click="$emit('deleteRoom', item.id)"
                  >
                    <font-awesome-icon icon="trash" style="color:#d9534f"></font-awesome-icon>
                  </button>

                  <router-link
                    class="btn btn-sm btn-outline-secondary"
                    title="Check In"
                    :to="`/checkin/${user.uid}/${item.id}`"
                  >
                    <font-awesome-icon icon="user" style="color:#d9534f"></font-awesome-icon>
                  </router-link>

                  <router-link
                    class="btn btn-sm btn-outline-secondary"
                    title="Chat"
                    :to="`/chat/${user.uid}/${item.id}`"
                  >
                    <font-awesome-icon icon="video" style="color:#d9534f"></font-awesome-icon>
                  </router-link>
                </section>
                <div class="ml-3">{{ item.name }}</div>
              </section>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
export default {
  name: "Rooms",
  data: function () {
    return {
      roomName: null,
    };
  },
  components: {
    FontAwesomeIcon,
  },
  methods: {
    handleAdd: function () {
      this.$emit("addRoom", this.roomName);
      this.roomName = null;
      this.$refs.roomName.focus();
    },
  },
  props: ['rooms','user'],
};
</script>
<style type="text/css">
body {
  background: #5b5b5b !important;
}
</style>
