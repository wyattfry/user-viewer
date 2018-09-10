<template>
  <tr data-toggle="modal" data-target="#userDetailModal" style="cursor:pointer;" @click="handleClick(user.id)">
    <td>{{ user.id }}</td>
    <td>{{ user.name }}</td>
    <td>{{ user.email }}</td>
    <td>{{ user.phone }}</td>
  </tr>
</template>

<script>
export default {
  name: 'UserRow',
  props: {
    user: Object,
  },
  methods: {
    handleClick: function (id) {
      this.$emit('rowClick', id);
    }
  }
};
</script>
