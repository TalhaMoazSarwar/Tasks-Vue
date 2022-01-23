<template>
  <div class="mt-3">
    <Task
      v-for="task in tasks"
      :task="task"
      :key="task.id"
      @removeTask="removeTask"
      @dblclick="toggleActive(task.id)"
    />
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
  components: {
    Task,
  },
  props: {
    task: Object,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    removeTask(id) {
      this.tasks = this.tasks.filter((v) => v.id !== id);
    },
    toggleActive(id) {
      this.tasks = this.tasks.map((v) =>
        v.id === id ? { ...v, active: !v.active } : v
      );
    },
  },
  watch: {
    task(task) {
      this.tasks.push(task);
    },
  },
};
</script>