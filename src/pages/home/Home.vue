<template>
  <site-template>
    <span slot="menu-esquerdo">
      <card-menu-vue>
        <div class="row valign-wrapper">
          <grid-vue tamanho="4">
            <img :src="usuario.imagem" :alt="usuario.name" class="circle responsive-img"> <!-- notice the "circle" class -->
          </grid-vue>
          <grid-vue tamanho="8">
            <span class="black-text">
              <h5>{{ usuario.name }}</h5>
            </span>
          </grid-vue>
        </div>
      </card-menu-vue>
      <card-menu-vue>
        Teste
      </card-menu-vue>
    </span>

    <span slot="principal">
      <publicar-conteudo-vue/>
      <conteudo-vue perfil="https://materializecss.com/images/yuna.jpg"
                    nome="Maria Silva" data="21/12/2019 10:45">
        <card-detalhe-vue imagem="https://materializecss.com/images/sample-1.jpg"
                          titulo="Titulo do card" conteudo="I am a very simple card. I am good at containing small bits of information.
            I am convenient because I require little markup to use effectively." />
      </conteudo-vue>
    </span>
  </site-template>
</template>

<script>
import SiteTemplate from "@/templates/SiteTemplate";
import ConteudoVue from "@/components/social/ConteudoVue";
import CardDetalheVue from "@/components/social/CardDetalheVue";
import PublicarConteudoVue from "@/components/social/PublicarConteudoVue";
import CardMenuVue from "@/components/layouts/CardMenuVue";
import GridVue from "@/components/layouts/GridVue";


export default {
  name: 'Home',
  components: {
    SiteTemplate,
    ConteudoVue,
    CardDetalheVue,
    PublicarConteudoVue,
    CardMenuVue,
    GridVue
  },
  data () {
    return {
      usuario: {}
    }
  },
  created() {
    let usuario = sessionStorage.getItem('usuario');
    if (usuario) {
      this.usuario = JSON.parse(usuario)
    }
  }
}
</script>


<style scoped>

</style>
