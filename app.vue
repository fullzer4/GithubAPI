<template>
  <div>
    <h1> Get github users </h1>
    <input type="text" v-model="userName" placeholder="github username">
    <button @click="fetchUser">Buscar</button>

    <UserInfo/>
  </div>
</template>

<script>

import UserInfo from "./components/UserInfo.vue"

export default {
  components: {
    UserInfo
  },
  data() {
    return {
      userName: ''
    };
  },
  methods: {
    fetchUser() {
      this.$refs.UserInfo.getGithubUser(this.userName);
    }
  }
};   
}
</script>
