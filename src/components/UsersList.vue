<template>
  <div>
    <h3>Список пользователей</h3>
    <UserItem
      v-for="user in users"
      v-bind:key="user.id"
      v-bind:user="user"
    ></UserItem>
  </div>
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
