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

export default {

  name: 'app',
  
  components: {
    Todos, 
    Header, 
    AddTodo
  }, 

  data() {
    return {
      todos: [
        {
          id:1, 
          title: 'One', 
          completed: true
        },
        {
          id:2, 
          title: 'Two', 
          completed: true
        },
        {
          id:3, 
          title: 'Three', 
          completed: false
        }
      ]
    }
  }, 

  methods: {
    
    deleteToDo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }, 

    addTodo(newToDo) {
            console.debug('Hello john')
             this.todos = [...this.todos, newToDo];
    }
  },


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
