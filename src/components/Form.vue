<template>
  <v-container id="form-container">
    <v-form id="form" @submit.prevent="emitAddTaskName">
      <v-text-field
        id="task-input"
        label="Task"
        v-model="taskName"
        :rules="[rules.required]"
        clearable
        clear-icon="fas fa-times"
      />
      <v-btn
        id="submit-btn"
        color="primary"
        elevation="5"
        fab
        @click="emitAddTaskEvent"
      >
        <v-icon>fas fa-plus</v-icon>
      </v-btn>
    </v-form>
  </v-container>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'

export default {
  name: 'Form',
  data: function () {
    return {
      taskName: '',
      rules: {
        required: (value) => !!value || 'Required.',
      },
    }
  },
  methods: {
    emitAddTaskEvent() {
      if (!this.taskName) {
        return
      }
      this.$emit('addTask', {
        id: uuidv4(),
        name: this.taskName,
        done: false,
      })
      this.taskName = ''
    },
  },
}
</script>

<style>
#form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

#form {
  display: flex;
  flex-direction: row;
  width: 70%;
  margin-top: 60px;
}

#submit-btn {
  margin-left: 10px;
}
</style>