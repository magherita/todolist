<template>
  <div id="app">
    <Header />

    <router-view></router-view>
  </div>
</template>

<script>
import Vue from "vue";
import Header from "./components/layouts/Header.vue";

const App = Vue.extend({
  components: { Header },
});

export default App;
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
</style>
