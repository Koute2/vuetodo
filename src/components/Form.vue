<template>
  <form action="/" method="post">
    <input type="text" v-model="body" />
    <button type="submit" @click.prevent="submit">+</button>
  </form>
</template>

<script>
import { ref } from "@vue/composition-api";

export default {
  setup(_, { emit }) {
    const body = ref("");

    const submit = () => {
      if (body.value.length === 0) return;
      emit("add", body.value);
      body.value = "";
    };

    return {
      body,
      submit
    };
  }
};
</script>
