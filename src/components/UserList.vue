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
        @remove-user="removeUser"
        :userForEdit="userForEdit"
        @edit-user="editThisUser"
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
    userForEdit: Object,
  },
  methods: {
    removeUser(user) {
      this.$emit("remove-user", user);
    },
    editThisUser(person) {
      this.$emit("edit-user", person);
    },
  },
};
</script>

<style scoped>
</style>