<template>
  <div class="flex flex-col mt-5">
    <label class="text-sm text-gray-600">Task</label>
    <input
      type="text"
      placeholder="Add Task"
      class="border p-1"
      v-model="name"
    />

    <p class="text-sm text-red-600" v-if="(message = hasError('name'))">
      {{ message }}
    </p>
  </div>
  <div class="flex flex-col mt-5">
    <label class="text-sm text-gray-600">Day & Time</label>
    <input
      type="datetime-local"
      placeholder="Add Task"
      class="border p-1"
      v-model="time"
    />
    <p class="text-sm text-red-600" v-if="(message = hasError('time'))">
      {{ message }}
    </p>
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
      errors: [],
    };
  },
  methods: {
    addTask() {
      if (this.formValidated()) {
        let data = {
          id: this.index++,
          text: this.name,
          date: this.time,
          active: true,
        };

        this.$emit("addTask", data);

        this.name = "";
        this.time = "";
      }
    },
    formValidated() {
      // validation
      this.errors = [];
      if (!this.name) {
        this.errors.push({
          name: "name",
          message: "This task name field is required!",
        });
      }

      if (!this.time) {
        this.errors.push({
          name: "time",
          message: "Please select day and time of the task!",
        });
      }

      if (!this.errors.length) {
        return true;
      }
    },
    hasError(v) {
      let error = this.errors.find((e) => e.name === v);
      return error ? error.message : false;
    },
  },
  emits: ["addTask"],
};
</script>