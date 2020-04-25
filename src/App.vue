<template>
  <div id="app">
      <h1> Witaj w systemie do zapisów na zajęcia </h1>
      <div v-if="authenticatedUsername == ''">
          <div> Zaloguj się e-mailem </div>
          <input type="email" v-model="email">
          <button @click="logMeIn()">Wchodzę</button>
      </div>
      <div v-else>
          <h2>Witaj {{email}}!</h2>
          <a href="" @click="logOut()">Wyloguj</a>
      </div>




  </div>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'


//to jest json
// {atrybut: wartosc, artu 2: wartosc2}

export default {
    data() {
        return {
            email:'',
            authenticatedUsername:''
        };
    },

    methods: {
        logMeIn() {
            this.authenticatedUsername = this.email;
        },
        logOut() {
            this.authenticatedUsername = '';
        }
    }
}
</script>

<style>
</style>
