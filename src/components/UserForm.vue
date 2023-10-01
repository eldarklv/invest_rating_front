<template>
  <form v-on:submit.prevent>
    <h4>Создать пользователя</h4>
    <input v-model="user.name" class="input" type="text" placeholder="Имя" />
    <input
      v-model="user.surname"
      class="input"
      type="text"
      placeholder="Фамилия"
    />
    <input v-model="user.city" class="input" type="text" placeholder="Город" />
    <button class="btn" v-on:click="createUser">Создать</button>
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

.btn {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}

form {
  display: flex;
  flex-direction: column;
}
</style>
