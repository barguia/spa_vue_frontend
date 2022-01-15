<template>
  <span>
    <header>
      <nav-bar-vue cor="blue">
        <li><router-link to="/">Home</router-link></li>
        <li>
          <router-link to="/perfil">{{ usuario.name }}</router-link>
        </li>
        <li><a @click="logout()">Sair</a></li>
      </nav-bar-vue>
    </header>
    <main class="container">
      <div class="row">
        <grid-vue tamanho="4">
          <slot name="menu-esquerdo"/>
        </grid-vue>
        <grid-vue tamanho="8">
          <slot name="principal"/>
        </grid-vue>
      </div>

    </main>

    <footer>
      <footer-vue logo="Social" descricao="Testes de descricao." ano="2018">
        <h5 class="white-text">Links</h5>
          <ul>
            <li><a class="grey-text text-lighten-3" href="#!">Página home</a></li>
            <li><a class="grey-text text-lighten-3" href="#!">Link 2</a></li>
            <li><a class="grey-text text-lighten-3" href="#!">Link 3</a></li>
            <li><a class="grey-text text-lighten-3" href="#!">Link 4</a></li>
          </ul>
      </footer-vue>
    </footer>

  </span>
</template>


<script>
import NavBarVue from '@/components/layouts/NavbarVue'
import FooterVue from '@/components/layouts/FooterVue'
import GridVue from "@/components/layouts/GridVue";

export default {
  name: 'SiteTemplate',
  components: {
    NavBarVue,
    FooterVue,
    GridVue
  },
  data() {
    return {
      usuario: false
    }
  },
  created() {
    let usuario = sessionStorage.getItem('usuario')
    if (usuario) {
      this.usuario = JSON.parse(usuario)
    } else {
      this.$router.push('/login')
    }
  },
  methods: {
    logout() {
      sessionStorage.clear();
      this.$router.push('/login')
      this.usuario = false;
    }
  }
}
</script>

<style>
</style>
