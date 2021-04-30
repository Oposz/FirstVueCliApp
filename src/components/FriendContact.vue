<template>
  <li>
    <h2>{{ friend.name }}{{ friend.isFavourite === true ? "(Favourite)" : "" }}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="toggleFavourite">
      {{ friend.IsFavourite ===true ? "Not Favourite" : "Favourite" }}
    </button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong>{{ friend.phone }}</li>
      <li><strong>Email:</strong>{{ friend.email }}</li>
    </ul>
  </li>
</template>

<script>
export default {

  props: {
      friend:{
          type:Object,
          required:true,
      },
  },
  emits:['toggle-favourite'],
  data() {
    return {
      detailsAreVisible: false,
    //   friend: {
    //     id: "manuel",
    //     name: "Manuel Lopez",
    //     phone: "3423423423423423",
    //     email: "manuel@gmail.com",
    //   },
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
        this.$emit('toggle-favourite',this.friend.id)
    },
  },
};
</script>

<style scoped>
</style>