<template>
  <div id="app">
    <h1 class="ui dividing centered header">Vue.js Todo App</h1>
    <div class='ui three column very relaxed grid main-content'>
      <div class='column'>
        <todo-list v-bind:todos="todos"></todo-list>
      </div>
      <div class="column">
        <create-todo v-on:create-todo="createTodo"></create-todo>
      </div>
      <div class="column">
        <completed-todo-list></completed-todo-list>
      </div>
    </div>
  </div>
</template>

<script>
import sweetalert from 'sweetalert'
import TodoList from './components/TodoList'
import CreateTodo from './components/CreateTodo'
import CompletedTodoList from './components/CompletedTodoList'
export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
    CompletedTodoList
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

<style>
  #app {
    padding: 30px;
  }

  .main-content {
    padding: 30px 0 !important;
  }
</style>
