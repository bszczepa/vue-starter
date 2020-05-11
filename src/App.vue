<template>
  <div id="app">
      <h1> Witaj w systemie do zapisów na zajęcia </h1>
      <div v-if="authenticatedUsername == ''">
          <login-form @login="logMeIn($event)"></login-form>
      </div>
      <div v-else>
          <logout-form :username="authenticatedUsername" @logout="logOut($event)"></logout-form>
      </div>

      <meeting-page>
      </meeting-page>
  </div>

</template>

<script>
import "milligram";
import LoginForm from "./components/LoginForm";
import LogoutForm from "./components/LogoutForm";
import MeetingPage from "./components/MeetingPage";
import NewMeetingForm from "./components/NewMeetingForm";
import MeetingsList from "./components/MeetingsList";

//to jest json
// {atrybut: wartosc, artu 2: wartosc2}

export default {
    components: {LoginForm, LogoutForm, MeetingPage, NewMeetingForm, MeetingsList},

    data() {
        return {
            authenticatedUsername:''
        };
    },

    methods: {
        logMeIn(username) {
            this.authenticatedUsername = username;
        },
        logOut(username) {
            this.authenticatedUsername = '';
        }
    }
}
</script>

<style>
</style>
