<template>
  <span>
    <div v-if="imagem" class="card-image">
        <img :src="imagem">
        <span class="card-title">{{ titulo }}</span>
      </div>

      <div v-if="conteudo" class="card-content">
        <p>{{ conteudo }}</p>
      </div>
  </span>
</template>

<script>
export default {
  name: "CardDetalheVue",
  props: ['imagem', 'titulo', 'conteudo']
}
</script>

<style scoped>

</style>
