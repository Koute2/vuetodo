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
  methods: {
    remove: function() {
      this.$emit("remove", this.todo.id);
    }
  }
};
</script>
