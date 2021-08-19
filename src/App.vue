<template>
  <div id="app">
    <div id="sidebar">
      <clock/>
      <hello/>
      <todoinput/>
      <todolist/>
    </div>
    <div id="container">
      <board/>
      <post/>
    </div>
  </div>
</template>

<script>
import clock from "./components/clock";
import hello from "./components/hello";
import todoinput from "./components/todoinput";
import todolist from "./components/todolist";
import board from "./components/board";
import post from "./components/post";

export default {
  name: "App",
  components: {
    clock,
    hello,
    todoinput,
    todolist,
    board,
    post
  }
};
</script>

<style>
  @import "./assets/style.css";
</style>
