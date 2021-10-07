<template>
  <v-container id="main-container">
    <v-row>
      <h1 id="title">Todo App</h1>
    </v-row>
    <v-row>
      <Form @addTask="addTask" />
    </v-row>
    <v-row id="tasks-container">
      <v-container v-for="task in tasks" :key="task.id">
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
      const taskExists = this.tasks.find(currentTask => currentTask.name === task.name)
      if (taskExists) {
        alert('Task already exists')
        return
      }
      this.tasks.push(task)
      localStorage.setItem("@TodoAppVue2:tasks", JSON.stringify(this.tasks))
    },
    deleteTask(task) {
      this.tasks = this.tasks.filter((currentTask) => currentTask.id !== task.id)
      localStorage.setItem("@TodoAppVue2:tasks", JSON.stringify(this.tasks))
    },
  },
  mounted() {
    this.tasks = JSON.parse(localStorage.getItem("@TodoAppVue2:tasks")) || []
  }
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
  margin-top: 30px;
}

.task {
  margin: 0;
}
</style>
