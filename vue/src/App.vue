<template>
  <div id="app">
    <div id="nav">
      <router-link v-bind:to="{ name: 'home' }"><img id="icon-header" src="..\src\assets\icon header.png" alt="icon"></router-link>
      <div id="links">
        <router-link v-bind:to="{ name: 'home' }" v-if="$store.state.token != ''">Home</router-link>&nbsp;&nbsp;&nbsp;
        <router-link id="lobby-tag" v-bind:to="{name: 'lobby'}" v-if="$store.state.token != ''">Lobby</router-link>&nbsp;&nbsp;&nbsp;
        <router-link id="leaderboard-tag" v-bind:to="{name: 'leaderboard'}" v-if="$store.state.token != ''">Leaderboard</router-link>&nbsp;&nbsp;&nbsp;
        <router-link v-bind:to="{ name: 'logout' }" v-if="$store.state.token != ''">Logout</router-link>
      </div>
    </div>
    <router-view />
  </div>
</template>


<style>
  #nav {
    margin-bottom: 2rem;
    padding-top:0.5rem;
    padding-bottom:0.5rem;
    text-align: center;
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    display: inline-flex;
    align-items: center;
    background: linear-gradient(#272727,#1f1f1f);
    width: 100%;
  }
  #nav img {
    height: 50px;
    margin-left: 40px;
    align-content: flex-start;
  }
  #nav #links {
    font-size: 0.9rem;
    display: flex;
    align-items: center;
    width:88vw;
    justify-content: center;
  }
   #nav #links a:hover {
     color: chartreuse;
   }
  #app {
    width: 100vw;
    height: 100vh;
    background: linear-gradient(#292929, #1b1b1b);
    font-family:Verdana, Geneva, Tahoma, sans-serif;
  }
  #nav a {
    text-decoration: none;
    color: white;
    font-size: 110%;
  }
  #nav p {
    text-decoration: none;
    color: white;
    font-size: 110%;
  }
  #nav > a:hover {
    text-decoration: none;
    color: rgb(56, 216, 56);
    font-size: 110%;
  }
  

  
  
</style>