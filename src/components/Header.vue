<template>
  <div class="header">
    <h2>{{ title }}</h2>
    <button @click="$emit('toogle-form')">
      <span v-if="!isShowing" class="greenButton">Add Task</span>
      <span v-else-if="isShowing" class="redButton">Close</span>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {},
  name: "Header",
  props: {
    title: String,
    isShowing: Boolean,
  },
  components: {},
};
</script>

<style lang="scss" scoped>
.header {
  display: flex;
  flex-direction: space-between;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 20px;
}
.redButton {
  background-color: rgb(145, 38, 38);
  color: whitesmoke;
  font-style: bold;
  border-radius: 3px;
  border: none;
  padding: 7px 9px;
}
.greenButton {
  background-color: rgb(25, 207, 25);
  color: whitesmoke;
  font-style: bold;
  border-radius: 3px;
  border: none;
  padding: 7px 9px;
}
button {
  background: transparent;
  border: none;
}
</style>