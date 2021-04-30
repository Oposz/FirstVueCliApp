<template>
  <li>
    <h2>{{ friend.name }}{{ friendIsFavourite === true ? "(Favourite)" : "" }}</h2>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="toggleFavourite">
      {{ friendIsFavourite ===true ? "Not Favourite" : "Favourite" }}
    </button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong>{{ friend.phone }}</li>
      <li><strong>Email:</strong>{{ friend.email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  // props:[
  //     'name',
  //     'phoneNumber',
  //     'emailAddress',
  //     'isFavourite'
  //     ],
  props: {
      friend:{
          type:Object,
          required:true,
      }
    // name: {
    //   type: String,
    //   required: true,
    // },
    // phoneNumber: {
    //   type: String,
    //   required: true,
    // },
    // emailAddress: {
    //   type: String,
    //   required: true,
    // },
    // isFavourite: {
    //   type: Boolean,
    //   required: false,
    //   default: false,
    //   validator: function (value) {
    //     return value === "1" || value === "0";
    //   },
    
  },
  data() {
    return {
      detailsAreVisible: false,
    //   friend: {
    //     id: "manuel",
    //     name: "Manuel Lopez",
    //     phone: "3423423423423423",
    //     email: "manuel@gmail.com",
    //   },
      friendIsFavourite: this.friend.isFavourite,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
        this.friendIsFavourite=!this.friendIsFavourite;
    },
  },
};
</script>

<style scoped>
</style>