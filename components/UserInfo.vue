<template>
  <div v-if="user">
  </div>
</template>

<script>

import axios from "axios"

export default {
  data() {
    return {
      user: null
    };
  },
  methods: {
    getGithubUser(name) {
      axios.get(`https://api.github.com/users/${name}`)
        .then(response => {
          this.user = response.data;
          console.log(this.user)  
        })
        .catch(error => {
          console.error(error);
        });
    }
  }
};
</script>
