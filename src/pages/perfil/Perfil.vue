<template>
  <site-template>
    <span slot="menu-esquerdo">
      <card-menu-vue>
        <img :src="usuario.imagem" alt=""
             class="responsive-img" width="100%">
      </card-menu-vue>
    </span>

    <span slot="principal">
      <h2>Perfil</h2>
      <input type="text" placeholder="Nome" v-model="usuario.name">
      <input type="text" placeholder="E-mail" v-model="usuario.email">

      <div class="file-field input-field">
        <div class="btn">
          <span>Imagem</span>
          <input type="file" @change="salvaImagem">
        </div>
        <div class="file-path-wrapper">
          <input class="file-path validate" type="text">
        </div>
      </div>

      <input type="text" placeholder="Senha" v-model="usuario.password">
      <input type="text" placeholder="Confirme sua senha" v-model="usuario.password_confirmation">
      <button class="btn" @click="perfil()">Atualizar</button>
    </span>
  </site-template>
</template>

<script>
import SiteTemplate from "@/templates/SiteTemplate";
import CardMenuVue from "@/components/layouts/CardMenuVue";

export default {
  name: "Perfil",
  data() {
    return {
      usuario: {},
      imagem: false
    }
  },
  created() {
    var usuario = sessionStorage.getItem('usuario');
    usuario = JSON.parse(usuario);

    if (usuario) {
      this.usuario = usuario;
    }
  },
  components: {
    SiteTemplate,
    CardMenuVue
  },
  methods: {
    salvaImagem(e) {
      let file = e.target.files || e.dataTransfer.files;

      if (!file.length) {
        console.log('saiu')
        return;
      }

      let reader = new FileReader();
      reader.onloadend = (e) => {
        this.imagem = e.target.result;
      }

      reader.readAsDataURL(file[0]);
    },
    perfil() {
      let config = {
        'headers': {
          'authorization': `Bearer ${this.usuario.token}`
        }
      };

      let parameters = {
        'name': this.usuario.name,
        'email': this.usuario.email,
        'password': this.usuario.password,
        'password_confirmation': this.usuario.password_confirmation,
        'imagem': this.imagem,
      };
      this.$http.put(this.$urlAPI+`users/${this.usuario.id})`, parameters, config)
        .then(response => {
          if (response.data.token) {
            this.usuario = response.data;
            sessionStorage.setItem('usuario', JSON.stringify(response.data));
          }
        })
      .catch(error => {
        console.log(error)
      })
    }
  }
}
</script>

<style scoped>

</style>
