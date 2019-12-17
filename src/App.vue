<template>
  <div id="app">
    <!-- Catch the del-todo event and call that message  -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>





<script>

/*eslint no-console: ["error", { allow: ["debug"] }] */
import Todos from './components/Todos.vue'

export default {

  name: 'app',
  
  components: {
    Todos
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
    deleteTodo(id) {
      console.debug('Hello john')
      this.todos = this.todos.filter(todo => todo.id !== id);
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
</style>
