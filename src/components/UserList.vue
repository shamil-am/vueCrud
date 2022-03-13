<template>
  <p v-if="userList.length === 0">List is empty</p>
  <table class="table table-info" v-else>
    <thead>
      <th>Name</th>
      <th>Username</th>
      <th>Company</th>
      <th>City</th>
      <th>Address</th>
      <th>Phone</th>
      <th></th>
    </thead>
    <tbody>
      <SingleUser
        v-for="user in userList"
        :key="user.id"
        :person="user"
      ></SingleUser>
    </tbody>
  </table>
</template>

<script>
import SingleUser from "./SingleUser.vue";
export default {
  name: "UserList",
  components: {
    SingleUser,
  },
  props: {
    userList: Array,
  },
  methods: {
    removeUser(user) {
      this.$emit("remove-user", user);
    },
  },
};
</script>

<style scoped>
</style>