<template>
  <div>
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:toggle-task-complete="toggleTaskComplete" v-on:revert-todo="revertTodo" v-for="todo in todos" :todo.sync="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >
import sweetalert from 'sweetalert'
import Todo from './Todo'
export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      sweetalert({
        title: 'Are you sure?',
        text: 'This task will be permanently deleted!',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#DD6B55',
        confirmButtonText: 'Yes, delete it!',
        closeOnConfirm: false
      },
      () => {
        const todoIndex = this.todos.indexOf(todo)
        this.todos.splice(todoIndex, 1)
        sweetalert('Deleted!', 'Your task has been deleted.', 'success')
      })
    },
    toggleTaskComplete (todo) {
      let todoIndex = this.todos.indexOf(todo)
      if (this.todos[todoIndex].done === !true) {
        this.todos[todoIndex].done = true
        sweetalert('Success!', 'Task completed!', 'success')
      } else {
        this.todos[todoIndex].done = false
        sweetalert('Oops!', 'Better luck this time', 'success')
      }
    }
  }
}
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>
