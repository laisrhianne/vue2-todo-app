<template>
  <v-container id="form-container">
    <v-text-field id="task-input" label="Task" />
    <v-btn id="submit-btn" color="primary" elevation="2" icon medium>
      <v-icon>fas fa-plus</v-icon>
    </v-btn>
  </v-container>
</template>

<script>
export default {
  name: 'Form',
  data: function () {
    return {
      inputValue: '',
    };
  },
};
</script>

<style>
#form-container {
  display: flex;
  flex-direction: row;
  width: 60%;
}
</style>