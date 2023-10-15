<template>
  <div v-show="users.length > 0">
    <h3>Список пользователей</h3>
    <UserItem
      v-for="user in users"
      v-bind:key="user._id"
      v-bind:user="user"
      v-on:remove="$emit('remove', user)"
    ></UserItem>
  </div>
  <h3 v-show="users.length === 0">Список пользователей пуст</h3>
</template>

<script>
import UserItem from "./UserItem.vue";

export default {
  props: {
    users: {
      type: Array,
      required: true,
    },
  },
  components: { UserItem },
};
</script>

<style></style>
