<template>
  <div class='ui centered card'>
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ todo.task }}
      </div>
      <div class='meta'>
          {{ todo.description }}
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class='right floated trash icon' v-on:click="deleteTodo(todo)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Task</label>
          <input type='text' v-model="todo.task" >
        </div>
        <div class='field'>
          <label>Description</label>
          <input type='text' v-model="todo.description" >
        </div>
        <div class='ui fluid buttons'>
          <button class='ui basic green button' v-on:click="hideForm">
            Confirm
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-on:click="toggleTaskComplete(todo)" v-show="!isEditing &&todo.done" disabled>
        Completed
    </div>
    <div class='ui bottom attached blue basic button' v-on:click="toggleTaskComplete(todo)" v-show="!isEditing && !todo.done">
        Pending
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['todo'],
    data () {
      return {
        isEditing: false
      }
    },
    methods: {
      toggleTaskComplete (todo) {
        this.$emit('toggle-task-complete', todo)
      },
      deleteTodo (todo) {
        this.$emit('delete-todo', todo)
      },
      showForm () {
        this.isEditing = true
      },
      hideForm () {
        this.isEditing = false
      }
    }
  }
</script>
