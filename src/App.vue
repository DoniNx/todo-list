<template>
  <div class="container bg-red-500">
    <Header
      @toogle-form="toogleForm"
      title="Task Tracker"
      :isShowing="isShowing"
    />
    <AddTask v-show="isShowing" @new-task="addTask" />
    <Tasks @deletetask="deleteTask" @unremind="unRemind" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/TasksComp.vue";
import AddTask from "./components/AddTask.vue";

export default {
  data() {
    return {
      tasks: [],
      isShowing: false,
    };
  },
  methods: {
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => {
          return task.id !== id;
        });
      }
    },
    unRemind(id) {
      this.tasks = this.tasks.map((task) => {
        return task.id === id ? { ...task, remendir: !task.remendir } : task;
      });
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    toogleForm() {
      this.isShowing = !this.isShowing;
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Kill my cat",
        date: "March 3rd at 1:30am",
        remendir: true,
      },
      {
        id: 2,
        text: "Charlie chaplin to maker",
        date: "March 5rd at 1:30am",
        remendir: true,
      },
      {
        id: 3,
        text: "Who is my bestfriend",
        date: "Spetember 3rd at 1:30am",
        remendir: false,
      },
      {
        id: 4,
        text: "Eat supper",
        date: "November 3rd at 1:30am",
        remendir: true,
      },
    ];
  },
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
};
</script>

<style scoped>
.container {
  border: gray solid 1px;
  border-radius: 5px;
  font-family: sans-serif;
  padding: 1em;
  display: flex;
  flex-direction: column;
}
</style>
