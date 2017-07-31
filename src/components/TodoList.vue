<template>
  <div>
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-for="todo in todos" :todo.sync="todo"></todo>
    <create-todo></create-todo>
  </div>
</template>

<script type="text/javascript">
  import Todo from './Todo'
  import CreateTodo from './CreateTodo'

  export default {
    props: [
      'todos'
    ],
    components: {
      Todo,
      CreateTodo
    }
  }
</script>

<style>

</style>
