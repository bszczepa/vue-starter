<template>
  <div id="app">
      <h1> Witaj w systemie do zapisów na zajęcia </h1>
      <div v-if="authenticatedUsername == ''">
          <login-form @login="logMeIn($event)"></login-form>
      </div>
      <div v-else>
          <logout-form :username="authenticatedUsername" @logout="logOut($event)"></logout-form>
      </div>
      <div v-show="authenticatedUsername != ''">
          <meeting-page :username="authenticatedUsername"></meeting-page>
      </div>

  </div>

</template>

<script>
import "milligram";
import LoginForm from "./components/LoginForm";
import LogoutForm from "./components/UserState";
import MeetingPage from "./components/MeetingPage";


//to jest json
// {atrybut: wartosc, artu 2: wartosc2}

export default {
    components: {LoginForm, LogoutForm, MeetingPage},

    data() {
        return {
            authenticatedUsername:'',
        };
    },

    methods: {
        logMeIn(username) {
            this.authenticatedUsername = username;
        },
        logOut(username) {
            this.authenticatedUsername = '';
        },

    }
}
</script>

<style>
</style>
