<template>
  <div>
    <h1>My shop</h1>
    <AddUser @form-submit="addNewUser" />
    <UserList
      :userList="userList"
      @remove-user="removeUser"
      :userForEdit="userForEdit"
      @edit-user="editThisUser"
      @save-update="saveUpdate"
      @cancel-editing="cancelEditing"
    />
  </div>
</template>

<script>
import AddUser from "./components/AddUser.vue";
import UserList from "./components/UserList.vue";
const API = "http://localhost:3000/users";
export default {
  name: "App",
  mounted() {
    this.getUsers(API);
  },
  data() {
    return {
      userList: [],
      userForEdit: {},
    };
  },
  components: {
    UserList,
    AddUser,
  },
  methods: {
    async removeUser(user) {
      let response = confirm(`Are u sure delete ${user.name} ?`);
      if (response) {
        let response = await fetch(`${API}/${user.id}`, {
          method: "DELETE",
        });
        if (response.ok) {
          // remove from UI
          this.userList = this.userList.filter((userL) => userL.id !== user.id);
          alert("Deleted!");
        }
      }
    },
    async addNewUser(newUser) {
      let response = await fetch(API, {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(newUser),
      });
      if (response.ok) {
        let newUser = await response.json();
        // add to UI
        this.userList = [...this.userList, newUser];
        alert("added");
      }
    },
    editThisUser(person) {
      this.userForEdit = person;
    },
    async saveUpdate(editingUser) {
      let response = await fetch(`${API}/${editingUser.id}`, {
        method: "PUT",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(editingUser),
      });
      if (response.ok) {
        //
        this.userList = this.userList.map((user) => {
          if (user.id === editingUser.id) {
            return editingUser;
          }
          return user;
        });
        this.userForEdit = {};
        alert("Edited!");
      }
    },
    cancelEditing() {
      this.userForEdit = {};
    },
    async getUsers(api) {
      let response = await fetch(api);
      let result = await response.json();
      this.userList = result;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
