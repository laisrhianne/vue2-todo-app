<template>
  <v-container id="main-container">
    <h1 id="title">Todo App</h1>
    <Form @addTask="addTask"/>
  </v-container>
</template>

<script>
import Form from '../components/Form.vue'
export default {
  name: 'Home',
  components: {
    Form
  },
  methods: {
    addTask(task) {
      console.log(task)
    }
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

  margin-top: 30px;
}
</style>
