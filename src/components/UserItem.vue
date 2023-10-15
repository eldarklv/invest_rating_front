<template>
  <div class="user">
    <div><strong>ID: </strong>{{ user._id }}</div>
    <div>
      <strong>Имя: </strong>
      {{ user.name }} {{ user.surname }}
    </div>
    <div><strong>Город: </strong>{{ user.city }}</div>
    <div><strong>Баллы: </strong>{{ user.scores }}</div>
    <div>
      <my-button v-on:click="$emit('remove', user)">Удалить</my-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
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
  display: flex;
  align-self: center;
  justify-content: space-between;
}
</style>
