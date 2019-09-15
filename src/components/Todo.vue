<template>
  <p class="todo">
    <button @click.prevent="remove">-</button>
    {{ todo.body }}
  </p>
</template>

<script>
export default {
  name: "Todo",
  props: {
    todo: {
      type: Object,
      required: true,
      default: () => {},
      validator: ({ id, body }) => {
        return typeof id === "number" && typeof body === "string";
      }
    }
  },
  setup({ todo }, { emit }) {
    const remove = () => {
      emit("remove", todo.id);
    };

    return {
      remove
    };
  }
};
</script>
