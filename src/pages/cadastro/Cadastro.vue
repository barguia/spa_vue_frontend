<template>
  <login-template>
    <span slot="menu-esquerdo">
      <CardMenuVue>
        <img src="https://prodoctor.net/blog/wp-content/uploads/2021/06/Novo-Projeto-58.png" alt=""
             class="responsive-img" width="100%">
      </CardMenuVue>

    </span>
    <span slot="principal">
      <h2>Cadastro</h2>
      <input type="text" placeholder="Nome" v-model="usuario.name">
      <input type="email" placeholder="E-mail" v-model="usuario.email">
      <input type="password" placeholder="Senha" v-model="usuario.password">
      <input type="password" placeholder="Confirme a senha" v-model="usuario.password_confirmation">
      <button class="btn" @click="cadastro()">Enviar</button>
      <router-link to="/login" class="btn orange">Já possuo cadastro</router-link>
    </span>

  </login-template>
</template>

<script>
import LoginTemplate from "@/templates/LoginTemplate";
import CardMenuVue from "@/components/layouts/CardMenuVue";

export default {
  name: "Cadastro",
  components: {
    LoginTemplate,
    CardMenuVue
  },
  data() {
    return {
      usuario:{}
    }
  },
  methods: {
    cadastro() {
      this.$http.post(this.$urlAPI+`users`, this.usuario)
        .then(response => {
          if (response.data.token) {
            sessionStorage.setItem('usuario', JSON.stringify(response.data))
            this.$router.push('/')
          }
        })
      .catch((error) => {
        console.log(error.response.status)
      })
    }
  }
}
</script>

<style scoped>

</style>
