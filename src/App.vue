<template>
  <div class="flex justify-center mt-5">
    <div class="w-96 border-2 p-4">
      <div class="flex justify-between items-center">
        <h1 class="text-2xl font-medium">Tasks Tracker</h1>
        <AddTaskToggle
          :status="showAddTask"
          @toggleAddTask="this.showAddTask = !this.showAddTask"
        />
      </div>
      <AddTask v-if="showAddTask" @addTask="addTask" />
      <Tasks :task="task" />
    </div>
  </div>
</template>

<script>
import AddTask from "./components/AddTask.vue";
import Tasks from "./components/Tasks.vue";
import AddTaskToggle from "./components/AddTaskToggle.vue";

export default {
  name: "App",
  components: {
    AddTask,
    Tasks,
    AddTaskToggle,
  },
  data() {
    return {
      showAddTask: true,
      task: null,
    };
  },
  methods: {
    addTask(data) {
      this.task = data;
    },
  },
};
</script>
