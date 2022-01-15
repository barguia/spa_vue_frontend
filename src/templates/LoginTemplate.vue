<template>
  <span>
    <header>
      <nav-bar-vue cor="blue">
        <li><router-link to="/login">Entrar</router-link></li>
        <li><router-link to="/cadastro">Cadastro</router-link></li>
      </nav-bar-vue>
    </header>
    <main class="container">
      <div class="row">
        <grid-vue tamanho="8">
          <slot name="menu-esquerdo"/>
        </grid-vue>
        <grid-vue tamanho="4">
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
  name: 'LoginTemplate',
  components: {
    NavBarVue,
    FooterVue,
    GridVue,
  }
}
</script>

<style>
</style>
