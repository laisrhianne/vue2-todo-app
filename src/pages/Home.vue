<template>
  <v-container id="main-container">
    <v-row>
      <h1 id="title">Todo App</h1>
    </v-row>
    <v-row>
      <Form @addTask="addTask" />
    </v-row>
    <v-row>
      <v-container id="tasks-container" v-for="task in tasks" :key="task.id">
        <Task class="task" :id="task.id" :title="task.name" :done="task.done" @deleteTask="deleteTask" />
      </v-container>
    </v-row>
  </v-container>
</template>

<script>
import Form from '../components/Form.vue'
import Task from '../components/Task.vue'
export default {
  name: 'Home',
  components: {
    Form,
    Task,
  },
  data() {
    return {
      tasks: [],
    }
  },
  methods: {
    addTask(task) {
      this.tasks.push(task)
    },
    deleteTask(task) {
      this.tasks = this.tasks.filter((currentTask) => currentTask.id !== task.id)
    },
  },
}
</script>

<style scoped>
#main-container {
  display: flex;
  flex-direction: column;
}

#title {
  width: 100%;
  text-align: center;

  margin-top: 60px;
}

#tasks-container {
  margin-top: 60px;
}

.task {
  margin: 0;
}
</style>
