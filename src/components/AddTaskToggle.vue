<template>
  <button
    type="button"
    class="px-2 py-1 text-white rounded"
    :class="statusClass"
    @click="toggleAddTask"
  >
    {{ statusText }}
  </button>
</template>

<script>
export default {
  props: {
    status: Boolean,
  },
  methods: {
    toggleAddTask() {
      this.$emit("toggleAddTask");
    },
  },
  computed: {
    statusClass() {
      return this.status
        ? "bg-red-600 hover:bg-red-700"
        : "bg-green-700 hover:bg-green-800";
    },
    statusText() {
      return this.status ? "Close" : "Add Task";
    },
  },
};
</script>