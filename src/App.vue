<template>
  <div id="app" class="wrapper">
    <h1>Форма регистрации нового клиента</h1>
    <ClientForm/>
  </div>
</template>

<script>
import ClientForm from './components/ClientForm.vue';

export default {
  name: 'App',
  components: {
    ClientForm,
  }
}
</script>