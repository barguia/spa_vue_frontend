<template>
  <div class="page-footer" :class="cor || 'blue'">
    <div class="container">
      <div class="row">
        <div class="col l6 s12">
          <h5 class="white-text">{{ logo || 'Site'}}</h5>
          <p class="grey-text text-lighten-4">{{ descricao }}</p>
        </div>
        <div class="col l4 offset-l2 s12">
          <slot></slot>
        </div>
      </div>
    </div>
    <div class="footer-copyright">
      <div class="container">
        © {{ano }} Copyright {{ logo || 'Site'}}
        <a class="grey-text text-lighten-4 right" href="#!">More Links</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FooterVue",
  props: ['cor', 'logo', 'descricao', 'ano']
}
</script>

<style scoped>

</style>
