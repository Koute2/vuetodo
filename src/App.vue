<template>
  <div id="app">
    <Form @add="addTodo" />
    <Todo
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @remove="removeTodo"
    />
  </div>
</template>

<script>
import Todo from "./components/Todo.vue";
import Form from "./components/Form.vue";

export default {
  name: "app",
  components: {
    Todo,
    Form
  },
  data: function() {
    return {
      nextId: 1,
      todos: []
    };
  },
  methods: {
    addTodo: function(text) {
      this.todos.unshift({
        id: this.nextId,
        body: text
      });
      this.nextId++;
    },
    removeTodo: function(target) {
      const idx = this.todos.findIndex(({ id }) => id === target);
      this.todos.splice(idx, 1);
    }
  }
};
</script>
