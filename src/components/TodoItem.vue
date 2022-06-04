<template>
  <div class="todo-item">
    <p>{{ todo.name }}</p>
    <span class="material-icons done" @click="deleteTodo"> done </span>
  </div>
</template>

<script>
export default {
  props: ["todo"],
  methods: {
    deleteTodo() {
      this.$emit("delete", this.todo.id);
    },
  },
};
</script>

<style>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: min(95%, 340px);
  height: 50px;
  margin: 10px auto;
  padding: 0 10px;
  border: 1px solid rgb(41, 41, 41);
  background: rgb(41, 41, 41);
  color: white;
  font-size: 14px;
}

.done {
  color: white;
  cursor: pointer;
}
</style>