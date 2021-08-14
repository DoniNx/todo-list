<template>
  <div>
    <form>
      Task:
      <input type="text" v-model="newTask.text" placeholder="Add Task" />
      <br />
      Date:
      <input type="date" v-model="date" placeholder="Enter date" />
      <input type="time" v-model="time" />
      <input type="checkbox" v-model="newTask.remendir" />: Remind me
    </form>
    <button @click="onSubmit">Add Task</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: {
        text: "",
        date: "",
        remendir: false,
      },
      date: "",
      time: "",
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (this.newTask.text === "") {
        alert("Enter some text");
        return;
      }
      this.newTask = {
        id: Math.floor(Math.random() * 1000000),
        ...this.newTask,
      };

      this.$emit("new-task", this.newTask);
    },
  },
  watch: {
    time: function () {
      this.newTask.date = this.date + " at " + this.time;
    },
    date: function () {
      this.newTask.date = this.date + " at " + this.time;
    },
  },
  name: "AddTask",
};
</script>




<style scoped>
</style>