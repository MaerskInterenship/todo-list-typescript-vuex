<template>
  <div id="completed-todos">
    <h3 v-if="completed.length > 0">Completed({{ completed.length }})</h3>
    <ul class="list1">
      <li class="listItem1" v-for="todo in completed" v-bind:key="todo.id">
        {{ todo.body }}
        <button type="button" @click="remove(todo)" class="btn">
          > > >
          <span class="remove"></span> Remove
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
