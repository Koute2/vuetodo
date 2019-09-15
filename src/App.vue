<template>
  <div id="app">
    <Form @add="addTodo" />
    <Todo
      v-for="todo in state.todos"
      :key="todo.id"
      :todo="todo"
      @remove="removeTodo"
    />
  </div>
</template>

<script>
import { reactive } from "@vue/composition-api";
import Todo from "./components/Todo.vue";
import Form from "./components/Form.vue";

export default {
  name: "app",
  components: {
    Todo,
    Form
  },
  setup() {
    const state = reactive({
      nextId: 1,
      todos: []
    });

    const addTodo = text => {
      state.todos.unshift({
        id: state.nextId,
        body: text
      });
      state.nextId++;
    };

    const removeTodo = target => {
      const idx = state.todos.findIndex(({ id }) => id === target);
      state.todos.splice(idx, 1);
    };

    return {
      state,
      addTodo,
      removeTodo
    };
  }
};
</script>
