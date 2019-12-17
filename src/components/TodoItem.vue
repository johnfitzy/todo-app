<template>
    <div>
        <h2>{{ todo.id + " " + todo.title }}</h2>
        <h3>{{ todo.completed }}</h3>
    </div>
</template>

<script>

export default {
    name: "TodoItem",
    props: ["todo"]
}

</script>

<style scoped>
    
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }

</style>