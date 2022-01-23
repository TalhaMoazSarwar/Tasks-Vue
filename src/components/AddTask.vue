<template>
  <div class="flex flex-col mt-5">
    <label class="text-sm text-gray-600">Task</label>
    <input
      type="text"
      placeholder="Add Task"
      class="border p-1"
      v-model="name"
    />
  </div>
  <div class="flex flex-col mt-5">
    <label class="text-sm text-gray-600">Day & Time</label>
    <input
      type="datetime-local"
      placeholder="Add Task"
      class="border p-1"
      v-model="time"
    />
  </div>
  <button class="bg-black text-white w-full mt-3 py-1" @click="addTask">
    Add Task
  </button>
</template>

<script>
export default {
  data() {
    return {
      index: 0,
      name: "",
      time: "",
    };
  },
  methods: {
    addTask() {
      let data = {
        id: this.index++,
        text: this.name,
        date: this.time,
        active: true,
      };
      this.name = "";
      this.time = "";
      this.$emit("addTask", data);
    },
  },
  emits: ["addTask"],
};
</script>