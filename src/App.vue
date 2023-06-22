<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/sobre">Sobre</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<style>

*{
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  background-color: #000000;
}

nav a {
  font-weight: bold;
  color: #836FFF;
}

nav a.router-link-exact-active {
  color: #836FFF;
}
</style>
