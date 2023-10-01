<template>
  <div class="app">
    <UserForm v-on:createUser="createUser"></UserForm>
    <UsersList v-bind:users="users"></UsersList>
  </div>
</template>

<script>
import UserForm from "./components/UserForm.vue";
import UsersList from "./components/UsersList.vue";

export default {
  components: {
    UserForm,
    UsersList,
  },
  data() {
    return {
      users: [
        {
          id: 1,
          name: "Eldar",
          surname: "Kuluev",
          city: "Oktyabrsky",
          scores: 14,
        },
        {
          id: 2,
          name: "John",
          surname: "Sina",
          city: "Las Vegas",
          scores: 20,
        },
        {
          id: 3,
          name: "Mark",
          surname: "Kotl",
          city: "New York",
          scores: 8,
        },
      ],
    };
  },
  methods: {
    createUser(user) {
      this.users.push(user);
    },
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
