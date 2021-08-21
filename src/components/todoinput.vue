<template>
  <input id="input" type="text" placeholder="Type your Todo" v-model="newTodo" v-on:keyup.enter="addTodo">
</template>

<script>
export default {
  data(){
    return{
      newTodo: ""
    };
  },
  methods: {
    addTodo(){
      if(this.newTodo !== ""){
        this.$emit("addTodo",this.newTodo);
        this.clearInput();
      }
    },
    clearInput(){
      this.newTodo = "";
    }
  }
}
</script>

<style>

</style>