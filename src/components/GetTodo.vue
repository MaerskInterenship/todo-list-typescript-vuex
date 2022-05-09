<template>
  <div id="get-todo" class="container">
    <input :value="newTodo" @change="getTodo" placeholder="I need to..." />
    <button class="btn3" @click="addTodo">Add Todo</button>
  </div>
</template>
<script>
export default {
  methods: {
    getTodo(e) {
      this.$store.dispatch("getTodo", e.target.value);
    },
    addTodo() {
      this.$store.dispatch("addTodo");
      this.$store.dispatch("clearTodo");
    },
  },
  computed: {
    newTodo() {
      return this.$store.getters.newTodo;
    },
  },
};
</script>
<style lang="scss">
.btn3 {
  background-color: rgb(0, 255, 234);
}
</style>
