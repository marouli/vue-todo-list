<template>
  <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
    <p class="title">
      <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed">
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
      </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
}
</script>

<style scoped>
  .todo-item {
    width: 50%;
    margin: 20px auto;
    padding: 16px;
    background: #f4f4f4;
    border-bottom: 1px #ccc dotted;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .title {
    font-size: 18px;
  }

  .title input {
    margin-right: 6px;
  }

  .del {
    background: #fa4949;
    color: #fff;
    border: none;
    font-size: 12px;
    padding: 4px 8px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>