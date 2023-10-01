<template>
  <div class="user" v-for="user in users" :key="user">
    <div>
      <strong>Имя: </strong>
      {{ user.name }} {{ user.surname }}
    </div>
    <div><strong>Город: </strong>{{ user.city }}</div>
    <div><strong>Баллы: </strong>{{ user.scores }}</div>
  </div>
</template>

<script>
export default {
  props: {
    users: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.user {
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
</style>
