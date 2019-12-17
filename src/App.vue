<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <!-- Catch the del-todo event and call that message  -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteToDo"/>
  </div>
</template>


<script>

/*eslint no-console: ["error", { allow: ["debug"] }] */

import Header from './components/layout/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import axios from 'axios';

export default {

  name: 'app',
  
  components: {
    Todos, 
    Header, 
    AddTodo
  }, 

  data() {
    return {
      todos: []
    }
  }, 

  methods: {
    
    deleteToDo(id) {


      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => this.todos =  this.todos.filter(todo => todo.id !== id))
        .catch(error => console.debug('An error happened ' + error));

    }, 

    addTodo(newTodo) {

        const {title, completed } = newTodo;

        // when you make a post request to /todos it gives you back the data that you sent
        axios.post('https://jsonplaceholder.typicode.com/todos', {
          title, 
          completed
        })
        .then(response => this.todos = [...this.todos, response.data])
        .catch(error => console.debug('An error happened ' + error));

      }
  },

  // this is like react component did mount
  created () {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
        .then(response => this.todos = response.data)
        .catch(error => console.debug('An error happened ' + error));
  }

}

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
  .btn:hover {
    background: #666;
  }
</style>
