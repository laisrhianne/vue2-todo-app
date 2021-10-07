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
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'Form',
  data: function () {
    return {
      taskName: '',
      rules: {
        required: value => !!value || 'Required.'
      },
    };
  },
  methods: {
    emitAddTaskEvent() {
      this.taskName = '';
      this.$emit('addTask', {
        taskName: this.taskName,
        id: uuidv4(),
        done: false,
      });
    },
  },
};
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
  margin-top: 30px;
}

#submit-btn {
  margin-left: 10px;
}
</style>