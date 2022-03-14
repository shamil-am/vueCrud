<template>
  <tr>
    <!-- name -->
    <td>
      <input
        v-if="userForEdit.id === person.id"
        type="text"
        v-model="editingUser.name"
        :readonly="false"
      />
      <input v-else type="text" v-model="editingUser.name" :readonly="true" />
    </td>
    <!-- username -->
    <td>
      <input
        v-if="userForEdit.id === person.id"
        type="text"
        v-model="editingUser.username"
        :readonly="false"
      />
      <input
        v-else
        type="text"
        v-model="editingUser.username"
        :readonly="true"
      />
    </td>
    <!-- company -->
    <td>
      <input
        v-if="userForEdit.id === person.id"
        type="text"
        v-model="editingUser.company.name"
        :readonly="false"
      />
      <input
        v-else
        type="text"
        v-model="editingUser.company.name"
        :readonly="true"
      />
    </td>

    <!-- city -->
    <td>
      <input
        v-if="userForEdit.id === person.id"
        type="text"
        v-model="editingUser.address.city"
        :readonly="false"
      />
      <input
        v-else
        type="text"
        v-model="editingUser.address.city"
        :readonly="true"
      />
    </td>

    <!-- street -->
    <td>
      <input
        v-if="userForEdit.id === person.id"
        type="text"
        v-model="editingUser.address.street"
        :readonly="false"
      />
      <input
        v-else
        type="text"
        v-model="editingUser.address.street"
        :readonly="true"
      />
    </td>
    <!-- phone -->
    <td>
      <input
        v-if="userForEdit.id === person.id"
        type="text"
        v-model="editingUser.phone"
        :readonly="false"
      />
      <input v-else type="text" v-model="editingUser.phone" :readonly="true" />
    </td>
    <!-- buttons -->
    <td v-if="userForEdit.id !== person.id">
      <button class="btn btn-danger" @click="removeUser(person)">X</button>
      <button class="btn btn-warning" @click="editThisUser(person)">
        Edit
      </button>
    </td>
    <td v-else>
      <button class="btn btn-success" @click="saveUpdate">Save</button>
      <button class="btn btn-light" @click="cancelEditing">Cancel</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "SingleUser",
  props: ["person", "test", "userForEdit"],
  data() {
    return {
      editingUser: {
        id: this.person.id,
        name: this.person.name,
        username: this.person.username,
        email: this.person.email,
        address: {
          street: this.person.address.street,
          suite: this.person.address.suite,
          city: this.person.address.city,
          zipcode: this.person.address.zipcode,
          geo: {
            lat: this.person.address.geo.lat,
            lng: this.person.address.geo.lng,
          },
        },
        phone: this.person.phone,
        website: this.person.website,
        company: {
          name: this.person.company.name,
          catchPhrase: this.person.company.catchPhrase,
          bs: this.person.company.bs,
        },
      },
    };
  },
  methods: {
    removeUser: function (person) {
      this.$emit("remove-user", person);
    },
    editThisUser(person) {
      this.$emit("edit-user", person);
    },
    saveUpdate() {
      this.$emit("save-update", this.editingUser);
    },
    cancelEditing() {
      this.$emit("cancel-editing");
    },
  },
};
</script>

<style scoped>
input:read-only {
  outline: none;
  border: none;
  background-color: transparent;
}
</style>