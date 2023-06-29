<template>
  <div v-if="user" ref="UserInfo">
    <div>
      <img :src="`${user.avatar_url}`" alt="Imagem do github" />
    </div>
    <div>
      <p>Nome: {{user.name}}</p>
      <p>Username: {{user.login}}</p>
      <p>Repositorios publicos: {{user.public_repos}}</p>
      <p>Localizacao: {{user.location}}</p>
      <p>Seguidores: {{user.followers}}</p>
      <p>Seguindo: {{user.following}}</p>
      <p>Link repos: <NuxtLink :to="`${user.repos_url}`">Link</NuxtLink></p>
    </div>
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
