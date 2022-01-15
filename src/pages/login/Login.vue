<template>
  <login-template>
    <span slot="menu-esquerdo">
      <card-menu-vue>
        <img src="https://prodoctor.net/blog/wp-content/uploads/2021/06/Novo-Projeto-58.png" alt=""
             class="responsive-img" width="100%">
      </card-menu-vue>

    </span>
    <span slot="principal">
      <h2>Login</h2>
        <input type="text" name="email" v-model="usuario.email">
        <input type="password" name="password" v-model="usuario.password">
        <button class="btn" @click="login()">Logar</button>
        <router-link to="/cadastro" class="btn orange">Cadastre-se</router-link>
    </span>


  </login-template>
</template>

<script>
import LoginTemplate from "@/templates/LoginTemplate";
import CardMenuVue from "@/components/layouts/CardMenuVue";

export default {
  name: "Login",
  components: {
    LoginTemplate,
    CardMenuVue
  },
  data() {
    return {
      usuario: {
        email: '',
        password: ''
      }
    }
  },
  created() {
    let usuario = sessionStorage.getItem('usuario')
    if (usuario) {
      this.$router.push('/')
    }
  },
  methods: {
    login() {
      this.$http.post(this.$urlAPI+`login`, this.usuario)
        .then(response => {
          if (response.data.token) {
            sessionStorage.setItem('usuario', JSON.stringify(response.data))
            this.$router.push('/')
          } else  {
            alert('Usuário ou senha inválida')
          }
        })
        .catch(function (error) {
          console.log('error')
        })
    }
  }
}
</script>

<style scoped>

</style>
