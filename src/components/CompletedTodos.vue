<template>
  <div id="completed-todos">
    <h3 v-if="completed.length > 0">Completed({{ completed.length }})</h3>
    <ul class="todos__list--completed">
      <li
        class="todos__list--item"
        v-for="todo in completed"
        v-bind:key="todo.id"
      >
        {{ todo.body }}
        <button
          type="button"
          @click="remove(todo)"
          class="todos__actions--completed"
        >
          > > > Remove
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  methods: {
    remove(todo) {
      this.$store.dispatch("removeTodo", todo);
    },
  },
  computed: {
    completed() {
      return this.$store.getters.completedTodos;
    },
  },
};
</script>
