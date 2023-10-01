<template>
  <form v-on:submit.prevent>
    <h3>Создать пользователя</h3>
    <input v-model="user.name" class="input" type="text" placeholder="Имя" />
    <input
      v-model="user.surname"
      class="input"
      type="text"
      placeholder="Фамилия"
    />
    <input v-model="user.city" class="input" type="text" placeholder="Город" />
    <my-button v-on:click="createUser" style="margin-top: 15px"
      >Создать</my-button
    >
  </form>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: "",
        surname: "",
        city: "",
      },
    };
  },
  methods: {
    createUser() {
      this.user.id = Date.now();
      this.$emit("createUser", this.user);
      this.user = {
        name: "",
        surname: "",
        city: "",
      };
    },
  },
};
</script>

<style>
.input {
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}

form {
  display: flex;
  flex-direction: column;
}
</style>
