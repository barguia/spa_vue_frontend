<template>
  <div class="row">
    <grid-vue class="input-field" tamanho="12">
      <textarea v-model="conteudo" class="materialize-textarea"></textarea>
      <label>O que está pegando</label>
    </grid-vue>
    <p>
      <grid-vue v-if="conteudo" tamanho="2 offset-s10" class="btn">Publicar</grid-vue>
    </p>

  </div>
</template>


<script>
import GridVue from '@/components/layouts/GridVue'
export default {
  name: "PublicarConteudo",
  props: ['perfil', 'nome', 'data'],
  components: {
    GridVue
  },
  data() {
    return {
      conteudo: ''
    }
  }
}
</script>

<style scoped>

</style>
