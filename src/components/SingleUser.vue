<template>
  <tr>
    <td>{{ person.name }}</td>
    <td>{{ person.username }}</td>
    <td>{{ person.company.name }}</td>
    <td>{{ person.address.city }}</td>
    <td>{{ person.address.street }}</td>
    <td>{{ person.phone }}</td>
    <td>
      <button class="btn btn-danger" @click="removeUser(user)">X</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "SingleUser",
  props: ["person"],
};
</script>

<style scoped>
</style>