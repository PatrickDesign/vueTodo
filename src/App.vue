<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Header />
    <Todos :todos="todos" @del-todo="deleteTodoItem"/>
    <AddTodo @add-todo="addTodo"/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

import Header from './components/layout/Header';

import axios from 'axios';

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  methods: {
    deleteTodoItem(IDToDelete)
    {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${IDToDelete}`)
        .then(res => this.todos = this.todos.filter(todo => todo.id != IDToDelete))
        .catch(err => console.log(err));
    },
    addTodo(newTodo)
    {
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {title, completed})
        .then(res => this.todos.push(res.data))
        .catch(err => consol.log(err));
    }
  },
  created()
  {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  },
  data(){
    return{
        todos: []
      // todos: [
      //   {
      //     id: 1,
      //     title: "Todo One",
      //     completed: false
      //   },
      //   {
      //     id: 2,
      //     title: "Todo Two",
      //     completed: true
      //   },
      //   {
      //     id: 3,
      //     title: "Todo Three",
      //     completed: false
      //   }
      // ]
    }
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */

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
  padding: 7 20;
  cursor: pointer;
}

.btn :hover {
  background: #555;
}

</style>
