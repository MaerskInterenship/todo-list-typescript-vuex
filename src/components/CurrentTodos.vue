<template>
  <div id="current-todos" class="container">
    <h3 v-if="todos.length > 0">Current({{ todos.length }})</h3>
    <ul class="todos__list--current">
      <li class="todos__list-item" v-for="todo in todos" v-bind:key="todo.id">
        {{ todo.body }}
        <div class="todos-actions">
          <button type="button" @click="edit(todo)" class="todos-actions--edit">
            Edit
          </button>
          <button
            type="button"
            @click="complete(todo)"
            class="todos-actions--complete"
          >
            Complete
          </button>
          <button
            type="button"
            @click="remove(todo)"
            class="todos-actions--remove"
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
.todos__list-item {
  display: flex;
  justify-content: space-between;
  padding-top: 10px;
}

.todos-actions {
  &--edit {
    background-color: #ffff00;
  }
  &--complete {
    background-color: #008000;
  }
  &--remove {
    background-color: #ff0000;
  }
}
</style>
