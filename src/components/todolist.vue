<template>
    <ul id="list">
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" v-on:click="removeTodo(todoItem, index)">
        {{todoItem}}
      </li>
    </ul>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    removeTodo(todoItem, index){
      this.$emit("remove",todoItem,index);
    }
  }
}
</script>

<style>

</style>