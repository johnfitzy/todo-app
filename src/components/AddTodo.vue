<template>
    <div>
        <form @submit.prevent="addTodo">
            <!-- v-model="title" binds it to teh data objects modal ref | @submit="addTodo" adds on submit trigger method addToDo(), need to pass it up 
                The reason why he didn't user @emit is because the local method addToDo will process some stuff and then emit up to App.vue
            -->
            <input type="text" name="title" placeholder="Add a todo" v-model="title">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>    
</template>

<script>

/*eslint no-console: ["error", { allow: ["debug"] }] */

import uuid from 'uuid';


export default {
    
    name: "AddTodo", 
    
    data() {
        return {
            title: ''
        }
    }, 

    methods: {
        addTodo() {
       
        
            const newTodo = {
                id: uuid.v4(), 
                title: this.title, 
                completed: false
            }

            console.debug(newTodo)


            // send up to parent
            this.$emit('add-todo', newTodo);

            this.title = '';
        }
    }
}
</script>

<style scoped>
 form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>