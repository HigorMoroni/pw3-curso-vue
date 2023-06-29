<template>
  <div>
    <AppButton @update="getUpdate">Save</AppButton>
    <button @click="showAppHook = !showAppHook">Trocar Status</button>
    {{ fullName }}
    <AppHook v-if="showAppHook" />
    <button @click="changeName">Alterar Nome</button>
    <img alt="Vue logo" src="./assets/logo.png">
  </div>
</template>

<script>
import AppButton from './components/AppButton';
import AppHook from './components/AppHook';

import { ref } from '@vue/reactivity';
import { computed, watch } from '@vue/runtime-core';

export default {
  name: 'App',

  components: {
    AppButton,
    AppHook
  },

  setup() {
    // DATA
    const user = ref({
      firstName: 'Jon',
      lastName: 'Snow'
    });

    const showAppHook = ref(false);

    // COMPUTEDS
    const fullName = computed(() => {
      return `${user.value.firstName} ${user.value.lastName}`;
    });

    // METHODS
    const getUpdate = data => {
      console.log('getUpdate', data);
    }
    const changeName = () => {
      user.value.firstName = 'Novo';
    }

    // WATCH
    watch(user, () => {
      console.log('Algo foi alterado no objeto');
    }, { deep: true });
    watch(() => user.value.firstName, () => {
      console.log('Alterou o primeiro nome');
    });

    // RETURN OBRIGATÓRIO
    return {
      user,
      changeName,
      fullName,
      showAppHook,
      getUpdate
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#app div {
  display: flex;
  flex-direction: column;
}
</style>
