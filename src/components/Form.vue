<template>
  <v-container id="form-container">
    <v-text-field id="task-input" v-model="taskName" label="Task" clearable clear-icon="fas fa-times"/>
    <v-btn id="submit-btn" color="primary" elevation="5" fab @click="emitAddTaskEvent">
      <v-icon>fas fa-plus</v-icon>
    </v-btn>
  </v-container>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'Form',
  data: function () {
    return {
      taskName: '',
    };
  },
  methods: {
    emitAddTaskEvent() {
      this.taskName = ''
      this.$emit('addTask', { taskName: this.taskName, id: uuidv4(), done: false });
    }
  }
};
</script>

<style>
#form-container {
  display: flex;
  flex-direction: row;
  width: 60%;
  margin-top: 30px;
}

#submit-btn {
  margin-left: 10px;
}
</style>