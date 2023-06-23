<template>
  <div class="usuario">
    <h2>Usuário</h2>
    <hr>
    <ul class="lista">
      <router-link tag="li" class="item-lista" to="/usuario/1">Usuário 1</router-link>
      <router-link tag="li" class="item-lista" to="/usuario/2">Usuário 2</router-link>
      <router-link tag="li" class="item-lista" to="/usuario/3">Usuário 3</router-link>
    </ul>
    <hr>
    {{ 'Completo: ' + $route.query.completo }}
    {{ 'Idioma: ' + $route.query.idioma }}
    <hr>
    <router-view></router-view>
    <hr>
    <button sucesso @click="irParaInicio">Voltar</button>
  </div>
</template>

<script>
export default {
  methods: {
    irParaInicio() {
      this.$router.push({name: 'inicio'});
    }
  }
}
</script>