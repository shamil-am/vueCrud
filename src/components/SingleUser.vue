<template>
  <tr>
    <td>{{ person.name }}</td>
    <td>{{ person.username }}</td>
    <td>{{ person.company.name }}</td>
    <td>{{ person.address.city }}</td>
    <td>{{ person.address.street }}</td>
    <td>{{ person.phone }}</td>
    <td>
      <button class="btn btn-danger" @click="removeUser(person)">X</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "SingleUser",
  props: ["person", "test"],
  methods: {
    removeUser(person) {
      this.$emit("remove-user", person);
    },
  },
};
</script>

<style scoped>
</style>