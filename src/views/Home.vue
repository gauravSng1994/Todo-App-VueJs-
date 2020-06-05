<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
  import Todos from "../components/Todos";
  import AddTodo from "../components/AddTodo";
  export default {
    name: 'App',
    components: {
      Todos,
      AddTodo
    },
    data(){
      return{
        todos:[
          { id:1, title:'Todo One', completed:false },
          { id:2, title:'Todo Two', completed:true },
          { id:3, title:'Todo Three', completed:false }
        ]
      }
    },
    methods:{
      deleteTodo(id){
        this.todos = this.todos.filter(todo => todo.id !== id);
      },
      addTodo(todo){
        this.todos = [...this.todos, todo];
      }
    }
  }
</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body{
    font-family: Arial, Helvetica, sans-serif;
    line-heignt:1.4;
  }
  .btn{
    display: inline-block;
    border:none;
    background: #555;
    color:#fff;
    padding: 7px 20px;
    cursor: pointer;
    outline: none;
  }
  .btn:active{
    display: inline-block;
    border:none;
    background: #555;
    color:#fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  /*.btn:hover{*/
  /*  background: #6660;*/
  /*}*/
</style>
