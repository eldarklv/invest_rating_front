<template>
  <form v-on:submit.prevent>
    <h3>Создать пользователя</h3>
    <my-input v-model="user.name" type="text" placeholder="Имя" />
    <my-input v-model="user.surname" type="text" placeholder="Фамилия" />
    <my-input v-model="user.city" type="text" placeholder="Город" />
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
      this.user._id = Date.now();
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
form {
  display: flex;
  flex-direction: column;
}
</style>
