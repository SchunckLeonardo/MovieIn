<template>
  <div id="app">
    <navHeader/>
    <mainMovies/>
  </div>
</template>

<script>
import navHeader from "./components/navHeader";
import mainMovies from "./components/mainMovies";

export default {
  name: "App",
  components: {
    navHeader,
    mainMovies
  }
};
</script>

<style>
#app {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  background-color: #181818;
  text-align: center;
}
</style>
