<template>
  <div class="usuario-detalhe">
    <h3>Usuário Detalhe</h3>
    <p><strong>Codigo:</strong> {{id}}</p>
    <!-- <button sucesso @click="$router.push('/usuario')">Voltar</button> -->
  </div>
</template>

<script>
export default {
    props: ['id'],
}
</script>