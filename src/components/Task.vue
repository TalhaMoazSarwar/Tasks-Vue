<template>
  <div
    class="bg-gray-200 px-3 py-1 mt-2 flex justify-between items-center"
    :class="{ 'border-l-4 border-l-green-800': task.active }"
  >
    <div class="">
      <h3 class="font-medium">{{ task.text }}</h3>
      <p class="text-sm">
        {{ new Date(task.date).toLocaleString() }}
      </p>
    </div>
    <div class="text-red-800 font-bold">
      <a href="#" @click.prevent="removeTask(task.id)">x</a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    task: Object,
  },
  methods: {
    removeTask(id) {
      this.$emit("removeTask", id);
    },
  },
};
</script>