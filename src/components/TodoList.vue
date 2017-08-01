<template>
  <div>
    <p class="tasks">Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-on:revert-todo="revertTodo" v-for="todo in todos" :todo.sync="todo"></todo>
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
        text: 'This Task will be permanently deleted!',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#DD6B55',
        confirmButtonText: 'Yes, delete it!',
        closeOnConfirm: false
      },
      () => {
        const todoIndex = this.todos.indexOf(todo)
        this.todos.splice(todoIndex, 1)
        sweetalert('Deleted!', 'Your Task has been deleted.', 'success')
      })
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
      sweetalert('Success!', 'Task completed!', 'success')
    },
    revertTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = false
      sweetalert('Oops!', 'Better luck this time', 'success')
    }
  }
}
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>
