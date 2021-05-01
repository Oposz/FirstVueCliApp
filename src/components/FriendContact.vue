<template>
  <li>
    <h2>
      {{ friend.name }}{{ friend.isFavourite === true ? "(Favourite)" : "" }}
    </h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="toggleFavourite">
      {{ friend.IsFavourite === true ? "Not Favourite" : "Favourite" }}
    </button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong>{{ friend.phone }}</li>
      <li><strong>Email:</strong>{{ friend.email }}</li>
    </ul>
    <button @click="$emit('delete',friend.id)">Delete</button>
  </li>
</template>

<script>
export default {
  components: {
  },
  props: {
    friend: {
      type: Object,
      required: true,
    },
  },
  emits: ["toggle-favourite","delete"],
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
      this.$emit("toggle-favourite", this.friend.id);
    },
    
  },
};
</script>

<style scoped>
</style>