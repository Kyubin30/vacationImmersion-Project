<template>
  <div id="app">
    <div id="sidebar">
      <clock/>
      <hello v-on:addName="addName"/>
      <todoinput v-on:addTodo="addTodoItem"/>
      <todolist v-bind:propsdata="todoItems" v-on:remove="removeTodoItem"/>
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
  },
  data(){
    return{
      todoItems: []
    };
  },
  created(){
    if(localStorage.length > 0){
      for(let i = 0; i < localStorage.length; i++){
        if(localStorage.key(i) !== "loglevel:webpack-dev-server" && localStorage.key(i) !== "name"){
          this.todoItems.push(localStorage.getItem(localStorage.key(i)));
        }
      }
    }
  },
  methods: {
    addName(name){
      localStorage.setItem("name",name);
    },
    addTodoItem(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodoItem(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    }
  }
};
</script>

<style>
  @import "./assets/style.css";
</style>
