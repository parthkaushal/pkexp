<template>
  <v-alert>Hare Krishna {{version}}</v-alert>
  <v-btn @click="login()">Login</v-btn>
  <v-btn @click="logOut()">Logout</v-btn>
</template>

<script setup>
import Moralis from 'Moralis'
// connect to Moralis server

const serverUrl = "https://bmqo8d2tvbzr.usemoralis.com:2053/server";
const appId = "BiO0g3AGggsWXVvvTWpCamBpMnP5tNHNo4DaApUo";
Moralis.start({ serverUrl, appId });

// add from here down
async function login() {
  let user = Moralis.User.current();
  if (!user) {
    user = await Moralis.authenticate();
  }
  console.log("logged in user:", user);
}

async function logOut() {
  await Moralis.User.logOut();
  console.log("logged out");
}


const version = 2 + 1
</script>