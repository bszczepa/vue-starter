<template>
  <div id="app">
      <h1> Twój email to: {{ email }} </h1>
      <div v-if="email.length < 10">Ale masz krótki adres!</div>
      <div v-else-if="email.length < 15">Twój adres e-mail jest w sam raz.</div>
      <div v-else>Twój adres e-mail jest stanowczo za długi.</div>
      <input type="text" v-model="email">
  </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'


//to jest json
// {atrybut: wartosc, artu 2: wartosc2}

export default {
  data() {
      return {
          email:''
      };
  }
}
</script>

<style>
</style>
