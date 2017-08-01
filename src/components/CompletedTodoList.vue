<template>
  <div>
    <p class="tasks">Completed Tasks: {{(todo => {return todo.done === true}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:toggle-task-complete="toggleTaskComplete" v-for="todo in todos" :todo.sync="todo.done"></todo>
  </div>

</template>

<script type="text/javascript">
  import sweetalert from 'sweetalert'
  import Todo from './Todo'
  export default {
    props: ['todos'],
    components: {
      Todo
    },
    methods: {
      toggleTaskComplete (todo) {
        let todoIndex = this.todos.indexOf(todo)
        if (this.todos[todoIndex].done === !true) {
          this.todos[todoIndex].done = true
          sweetalert('Success!', 'Task completed!', 'success')
        } else {
          this.todos[todoIndex].done = false
          sweetalert('Oops, task not completed!', 'Better luck next time', 'success')
        }
      }
    }
  }
</script>

<style>
  p.tasks {
    text-align: center;
  }
</style>
