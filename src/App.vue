<template>
  <div>
    <div id="header"></div>
    <div id="main-container">
      <h2>To Do's</h2>
      <TodoAdd v-on:add-todo="addTodo"/>
      <Todos v-bind:todoslist="copyTodos" v-on:delete-todo="deleteTodo"/>  
    </div>  
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
//import Search from './components/Search.vue'
import TodoAdd from './components/TodoAdd.vue'
import Todos from './components/Todos.vue'


export default {
  name: 'App',
  components: {
     Todos, TodoAdd
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id != id);
      this.copyTodos = [ ...this.todos];
    },
    addTodo(todo) {
      this.todos.push(todo);
      this.copyTodos = [ ...this.todos ];
    }
  },
  data(){
    return {
      todos: [
      {  id: 0,
        title: 'meditar en las mananas',
        completed: false
      },
      {  id: 1,
        title: 'comprar limones',
        completed: true
      },
      {  id: 2,
        title: 'pasear el perro imaginario',
        completed: false
      },
      {  id: 3,
        title: 'planificar cumple',
        completed: false
      }
      ],
      copyTodos: []
    }
  },
  created(){
    this.copyTodos = [ ...this.todos];
  }
}
</script>

<style>
*{
  box-sizing: border-box;
}

body{
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1.5em;
  padding: 0;
  margin: 0;
}

#main-container{
  border: solid 1px #ccc;
  width: 600px;
  margin: 100px auto;
}

#header{
  background: black;
  padding: 10px;
}

h2{
  padding: 0 10px;
}
</style>
