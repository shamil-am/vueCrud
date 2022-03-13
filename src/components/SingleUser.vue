<template>
  <tr>
    <!-- name -->
    <td v-if="userForEdit.id === person.id" contenteditable="true">
      {{ person.name }}
    </td>
    <td v-else contenteditable="false">{{ person.name }}</td>
    <!-- username -->
    <td v-if="userForEdit.id === person.id" contenteditable="true">
      {{ person.username }}
    </td>
    <td v-else contenteditable="false">
      {{ person.username }}
    </td>
    <!-- company -->
    <td v-if="userForEdit.id === person.id" contenteditable="true">
      {{ person.company.name }}
    </td>
    <td v-else contenteditable="false">
      {{ person.company.name }}
    </td>
    <!-- city -->
    <td v-if="userForEdit.id === person.id" contenteditable="true">
      {{ person.address.city }}
    </td>
    <td v-else contenteditable="false">
      {{ person.address.city }}
    </td>
    <!-- street -->
    <td v-if="userForEdit.id === person.id" contenteditable="true">
      {{ person.address.street }}
    </td>
    <td v-else contenteditable="false">{{ person.address.street }}</td>
    <!-- phone -->
    <td v-if="userForEdit.id === person.id" contenteditable="true">
      {{ person.phone }}
    </td>
    <td v-else contenteditable="false">{{ person.phone }}</td>
    <!-- buttons -->
    <td v-if="userForEdit.id !== person.id">
      <button class="btn btn-danger" @click="removeUser(person)">X</button>
      <button class="btn btn-warning" @click="editThisUser(person)">
        Edit
      </button>
    </td>
    <td v-else>
      <button class="btn btn-success">Save</button>
      <button class="btn btn-light">Cancel</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "SingleUser",
  props: ["person", "test", "userForEdit"],
  // props: {
  //   editThisUser: Object,
  // },
  methods: {
    removeUser(person) {
      this.$emit("remove-user", person);
    },
    editThisUser(person) {
      this.$emit("edit-user", person);
    },
  },
};
</script>

<style scoped>
</style>