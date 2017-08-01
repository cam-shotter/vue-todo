<template>
  <div id="app">
    <h1 class="ui dividing centered header">Vue.js Todo App</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:create-todo="createTodo"></create-todo>
      </div>
    </div>
  </div>
</template>

<script>
import sweetalert from 'sweetalert'
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'
export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo
  },
  data () {
    return {
      todos: [{
        task: 'Task A',
        description: 'Do thing A',
        done: false
      }, {
        task: 'Task B',
        description: 'Do thing B',
        done: true
      }, {
        task: 'Task C',
        description: 'Do thing C',
        done: false
      }, {
        task: 'Task D',
        description: 'Do thing D',
        done: false
      }]
    }
  },
  methods: {
    createTodo (newTodo) {
      this.todos.push(newTodo)
      sweetalert('Success!', 'To-Do created!', 'success')
    }
  }
}
</script>
