<template>
  <div id="current-todos" class="container">
    <h3 v-if="todos.length > 0">Current({{ todos.length }})</h3>
    <ul class="current-todos--list">
      <li
        class="current-todos--listItem"
        v-for="todo in todos"
        v-bind:key="todo.id"
      >
        {{ todo.body }}
        <div class="current-todos--btnGroup">
          <button type="button" @click="edit(todo)" class="current-todos--btn">
            Edit
          </button>
          <button
            type="button"
            @click="complete(todo)"
            class="current-todos--btn1"
          >
            Complete
          </button>
          <button
            type="button"
            @click="remove(todo)"
            class="current-todos--btn2"
          >
            Remove
          </button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  methods: {
    edit(todo) {
      this.$store.dispatch("editTodo", todo);
    },
    complete(todo) {
      this.$store.dispatch("completeTodo", todo);
    },
    remove(todo) {
      this.$store.dispatch("removeTodo", todo);
    },
  },
  computed: {
    todos() {
      return this.$store.getters.todos;
    },
  },
};
</script>
<style lang="scss">
li.current-todos--listItem {
  list-style-type: circle;
}
.current-todos--btn {
  background-color: #ffff00;
}
.current-todos--btn1 {
  background-color: #008000;
}
.current-todos--btn2 {
  background-color: #ff0000;
}

.current-todos--listItem {
  display: flex;
  justify-content: space-between;
  padding-top: 10px;
}
</style>
