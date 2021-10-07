<template>
  <v-card id="card">
    <v-card-title id="card-title">
      <v-container id="title-container">
        <v-checkbox v-model="done"></v-checkbox>
        <span id="title">{{ title }}</span>
      </v-container>
      <v-btn icon color="#F6F6F6" @click="emitDeleteTaskEvent">
        <v-icon color="error" medium>fas fa-trash</v-icon>
      </v-btn>
    </v-card-title>
  </v-card>
</template>

<script>
export default {
  name: 'Task',
  props: {
    id: String,
    title: String,
    done: Boolean,
  },
  methods: {
    emitDeleteTaskEvent() {
      this.$emit('deleteTask', { id: this.id })
    }
  }
}
</script>

<style>
#card {
  height: fit-content;
  padding: 0;
  margin: 0;
}

#card-title {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  flex-wrap: nowrap;
}

#title-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  padding: 0 10px;
}
</style>