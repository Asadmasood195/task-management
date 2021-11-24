<template>
  <header>
    <h1>{{ title }}</h1>
    <Button
      @btn-click="$emit('toggle-task')"
      :text="showAddTask ? 'Close Task ' : 'Add Task'"
      color="green"
    />
  </header>
  <AddTask v-show="showAddTask" @add-task="addTask" />
</template>

<script>
import Button from './Button.vue';
import AddTask from './AddTask.vue';

export default {
  name: 'Header',
  components: {
    Button,
    AddTask,
  },
  methods: {
    addTask(task) {
      this.$emit('add-task', task);
    },
  },
  props: {
    title: {
      type: String,
      default: 'default Title',
    },
    showAddTask: Boolean,
  },
  emits: ['add-task'],
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
