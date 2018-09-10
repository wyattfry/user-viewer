<template>
  <table class="table table-hover table-responsive user-table">
    <tbody>
      <tr>
        <th>#</th>
        <th>Name</th>
        <th>Email</th>
        <th>Phone</th>
      </tr>
      <tr is="user-row" v-for="user in users" :user="user" :key="user.id" v-on:rowClick="handleClick"></tr>
    </tbody>
  </table>
</template>

<script>

import UserRow from './UserRow.vue';

export default {
  name: 'UserTable',
  components: {
    'user-row': UserRow,
  },
  props: {
    users: Array,
  },
  data: () => ({
    counter: 0
  }),
  methods: {
    handleClick: function(id) {
      this.$emit('rowClick', id)
    }
  }
};
</script>
<style>
  table.user-table {
    text-align: left;
    display: inline;
  }
</style>