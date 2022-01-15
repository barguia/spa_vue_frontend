<template>
  <div class="row">
    <div class="card">
      <div class="card-content">
        <div class="row valign-wrapper">
          <grid-vue tamanho="1">
            <img :src="perfil" alt="" class="circle responsive-img">
          </grid-vue>
          <grid-vue tamanho="11">
              <span class="black-text">
                <strong>{{ nome }}</strong> <small>{{ data }}</small>
              </span>
          </grid-vue>
        </div>

          <slot></slot>
      </div>

      <div class="card-action">
        <p>
          <i class="material-icons">favorite_border</i>
          <i class="material-icons">insert_comment</i>
        </p>
      </div>

    </div>
  </div>
</template>


<script>
import GridVue from '@/components/layouts/GridVue'

export default {
  name: "ConteudoVue",
  props: ['perfil', 'nome', 'data'],
  components: {
    GridVue
  }

}
</script>

<style scoped>

</style>
