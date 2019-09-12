<template>
  <form action="/" method="post">
    <input type="text" v-model="body" />
    <button type="submit" @click.prevent="submit">+</button>
  </form>
</template>

<script>
export default {
  data: function() {
    return {
      body: ""
    };
  },
  methods: {
    submit: function() {
      if (this.body.length === 0) return;
      this.$emit("add", this.body);
      this.body = "";
    }
  }
};
</script>
