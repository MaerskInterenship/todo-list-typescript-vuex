<template>
  <div id="current-todos" class="container">
    <h3 v-if="todos.length > 0">Current({{ todos.length }})</h3>
    <ul class="list">
      <li class="listItem" v-for="todo in todos" v-bind:key="todo.id">
        {{ todo.body }}
        <div class="btnGroup">
          <button type="button" @click="edit(todo)" class="btn">
            <span class="edit"></span> Edit
          </button>
          <button type="button" @click="complete(todo)" class="btn1">
            <span class="complete"></span> Complete
          </button>
          <button type="button" @click="remove(todo)" class="btn2">
            <span class="remove"></span> Remove
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
.btnGroup {
  float: right;
}
.btn {
  background-color: yellow;
}
.btn1 {
  background-color: green;
}
.btn2 {
  background-color: red;
}
.list {
  display: block;
  list-style-type: disc;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  padding-inline-start: 40px;
}
</style>
