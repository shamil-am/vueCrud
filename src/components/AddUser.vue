<template>
  <form action="" class="form" @submit.prevent="handleSubmit">
    <div class="form-control">
      <label for="name">Name</label>
      <input type="text" name="name" id="name" v-model="newUser.name" />
    </div>
    <div class="form-control">
      <label for="username">Username</label>
      <input
        type="text"
        name="username"
        id="username"
        v-model="newUser.username"
      />
    </div>
    <div class="form-control">
      <label for="company">Company</label>
      <input
        type="text"
        name="company"
        id="company"
        v-model="newUser.company.name"
      />
    </div>
    <div class="form-control">
      <label for="city">City</label>
      <input type="text" name="city" id="city" v-model="newUser.address.city" />
    </div>
    <div class="form-control">
      <label for="address">Street</label>
      <input
        type="text"
        name="address"
        id="address"
        v-model="newUser.address.street"
      />
    </div>
    <div class="form-control">
      <label for="phone">Phone</label>
      <input type="text" name="phone" id="phone" v-model="newUser.phone" />
    </div>
    <button type="submit" class="btn btn-success">Add</button>
  </form>
</template>

<script>
export default {
  name: "AddUser",
  data() {
    return {
      newUser: {
        id: Date.now(),
        name: "",
        username: "",
        email: "",
        address: {
          street: "",
          suite: "",
          city: "",
          zipcode: "",
          geo: {
            lat: "",
            lng: "",
          },
        },
        phone: "",
        website: "",
        company: {
          name: "",
          catchPhrase: "",
          bs: "",
        },
      },
    };
  },
  methods: {
    handleSubmit() {
      // forward to parent
      this.$emit("form-submit", this.newUser);
      //reset fields
      this.newUser = {
        id: Date.now(),
        name: "",
        username: "",
        email: "",
        address: {
          street: "",
          suite: "",
          city: "",
          zipcode: "",
          geo: {
            lat: "",
            lng: "",
          },
        },
        phone: "",
        website: "",
        company: {
          name: "",
          catchPhrase: "",
          bs: "",
        },
      };
    },
  },
};
</script>
<style scoped>
.form {
  max-width: 400px;
  margin: 2rem auto;
}
.form-control {
  display: flex;
  flex-direction: column;
  padding: 1rem;
}
</style>
