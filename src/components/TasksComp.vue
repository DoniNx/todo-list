<template>
  <div>
    <div
      class="card"
      v-for="task in tasks"
      :key="task.id"
      :class="{ remendir: task.remendir }"
      @dblclick="$emit('unremind', task.id)"
    >
      <h3>
        {{ task.text }}
        <button @click="endTask(task.id)">done</button>
      </h3>
      <p>{{ task.date }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    endTask(id) {
      this.$emit("deletetask", id);
    },
  },
  name: "Task",
  components: {},
  props: {
    tasks: Array,
  },
};
</script>

<style lang="scss" scoped>
.card {
  border: solid gray 1px;
  border-radius: 3px;
  margin: 1em 0;
  padding: 0 5px;
  background: rgba(160, 160, 160, 0.527);
  user-select: none;
}
.remendir {
  border-left: green 5px solid;
}
h3 {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
</style>