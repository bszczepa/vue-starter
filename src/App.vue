<template>
  <div id="app">
      <h1> Witaj w systemie do zapisów na zajęcia </h1>
      <div v-if="authenticatedUsername == ''">
          <login-form @login="logMeIn($event)"></login-form>
      </div>
      <div v-else>
          <h2>Witaj {{authenticatedUsername}}!</h2>
          <a @click="logOut()">Wyloguj</a>
      </div>


  </div>

</template>

<script>
import "milligram";
import LoginForm from "./components/LoginForm";

//to jest json
// {atrybut: wartosc, artu 2: wartosc2}

export default {
    components: {LoginForm},

    data() {
        return {
            authenticatedUsername:''
        };
    },

    methods: {
        logMeIn(username) {
            this.authenticatedUsername = username;
        },
        logOut() {
            this.authenticatedUsername = '';
        }
    }
}
</script>

<style>
</style>
