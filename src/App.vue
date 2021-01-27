<template>
  <div id="app">
    <TopMenu></TopMenu>
    <img alt="Vue logo" src="./assets/logo.png" />
    <h2>Welcome to the Dark Palace</h2>
  </div>
</template>

<script>
import TopMenu from "./components/top-menu/TopMenu";

export default {
  name: "App",
  components: {
    TopMenu,
  },
};
</script>

<style lang="sass">
body
  background-color: #07001E
  margin: 0

#app
  font-family: Avenir, Helvetica, Arial, sans-serif
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  color: white
  font-size: 5.25vw
</style>
