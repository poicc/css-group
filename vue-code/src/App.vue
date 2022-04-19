<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/todoList">todoList</router-link> |
    <router-link to="/markRaw">markRaw</router-link> |
    <router-link to="/Counter">Counter</router-link> |
    <router-link to="/parent">slots</router-link> | 
    <router-link to="/slotName">slotName</router-link> |
    <router-link to="/slotScopes">slotScopes</router-link> |
    <router-link to="/dynamicArguments">DynamicArguments</router-link> |
    <router-link to="/globalApi">GlobalApi</router-link>|
    <router-link to="/transition">transition</router-link> |
    <router-link to="/tele">tele</router-link> |
    <router-link to="/async">async</router-link> |
    <router-link to="/async1">async1</router-link> 
  </nav>
  <router-view />
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
