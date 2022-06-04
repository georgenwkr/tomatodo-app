<template>
  <form @submit.prevent="addTodo">
    <input
      type="text"
      v-model="title"
      placeholder="What would you like to do?"
    />
    <button>add</button>
  </form>
  <div v-if="todos.length">
    <p v-if="todos.length === 5" class="ideal-msg">
      5 is the ideal amount of todos in a day, careful not to overwork yourself
    </p>
    <div v-for="todo in todos" :key="todo.id">
      <TodoItem :todo="todo" @delete="handleDelete" />
    </div>
  </div>
  <div v-else class="else-msg">
    <p>Add a todo</p>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  components: { TodoItem },
  data() {
    return {
      title: "",
      todos: [
        { name: "Study for psychology test", id: 2 },
        { name: "Finish work project", id: 1 },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.title.length) {
        this.todos = [{ name: this.title, id: Math.random() }, ...this.todos];
        this.title = "";
      }
    },
    handleDelete(id) {
      this.todos = this.todos.filter((todo) => {
        return todo.id !== id;
      });
    },
  },
};
</script>

<style>
form {
  text-align: center;
  border: 2px solid rgb(41, 41, 41);
  width: 350px;
  height: auto;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

form input {
  border: none;
  width: 300px;
  height: 40px;
  outline: none;
  padding: 0 10px;
  color: rgb(41, 41, 41);
  font-weight: 500;
}

form button {
  width: 50px;
  height: 42px;
  font-weight: 600;
  color: white;
  background: rgb(41, 41, 41);
  border: none;
  cursor: pointer;
}

.else-msg {
  text-align: center;
  color: rgb(23, 133, 23);
  font-weight: 400;
  font-size: 16px;
}

.ideal-msg {
  text-align: center;
  color: rgb(107, 107, 107);
  font-weight: 400;
  font-style: italic;
  font-size: 14px;
}
</style>