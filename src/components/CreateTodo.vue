<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Task</label>
            <input v-model="taskText" type='text'>
          </div>
          <div class='field'>
            <label>Description</label>
            <input v-model="descriptionText" type='text'>
          </div>
          <div class='ui buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      taskText: '',
      descriptionText: '',
      isCreating: false
    }
  },
  methods: {
    openForm () {
      this.isCreating = true
    },
    closeForm () {
      this.isCreating = false
    },
    sendForm () {
      if (this.taskText.length > 0 && this.descriptionText.length > 0) {
        const task = this.taskText
        const description = this.descriptionText
        this.$emit('create-todo', {
          task,
          description,
          done: false
        })
        this.taskText = ''
        this.descriptionText = ''
        this.isCreating = false
      }
    }
  }
}
</script>
