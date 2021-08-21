<template>
  <div id="hello" class="none">
    <div class="none" v-if="isName">Hello&nbsp;{{name}}!</div>
    <input class="none" id="hello" v-if="!isName" type="text" placeholder="What your name?" v-model="name" v-on:keyup.enter="addName">
  </div>
</template>

<script>
export default {
  data(){
    return{
      name: "",
      isName: false
    };
  },
  created(){
    if(localStorage.getItem("name")!==null){
      this.isName = true;
    }
  },
  methods: {
    addName(){
      if(this.name !== ""){
        this.$emit("addName",this.name);
        this.isName = true;
        this.clearInput();
      }
    },
    clearInput(){
      this.newTodo = "";
    }
  }
}
</script>