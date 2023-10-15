<template>
  <div class="app">
    <h1>Инвест рейтинг</h1>
    <my-button v-on:click="showDialog" style="margin: 15px 0"
      >Создать пользователя</my-button
    >
    <my-dialog v-model:show="dialogVisible">
      <UserForm v-on:createUser="createUser"></UserForm>
    </my-dialog>
    <UsersList
      v-bind:users="users"
      v-on:remove="removeUser"
      v-if="isUsersLoading === false"
    ></UsersList>
    <div v-else-if="isUsersLoading === true">Идет загрузка...</div>
  </div>
</template>

<script>
import axios from "axios";
import UserForm from "./components/UserForm.vue";
import UsersList from "./components/UsersList.vue";

export default {
  components: {
    UserForm,
    UsersList,
  },
  data() {
    return {
      users: [],
      dialogVisible: false,
      isUsersLoading: false,
    };
  },
  methods: {
    createUser(user) {
      this.users.push(user);
      this.dialogVisible = false;
    },
    removeUser(user) {
      this.users = this.users.filter((u) => u._id !== user._id);
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async getUsers() {
      try {
        this.isUsersLoading = true;
        const response = await axios.get("http://localhost:3000/users");
        this.users = response.data;
      } catch (error) {
        console.log(error);
      } finally {
        this.isUsersLoading = false;
      }
    },
  },
  mounted() {
    this.getUsers();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>

// single file component
