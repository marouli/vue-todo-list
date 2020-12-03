<template>
  <div id="app">
    <Header />
    <Todos 
      v-bind:todos="todos" 
      v-on:del-todo="deleteTodo"
    />
    <router-view />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
export default {
  name:"app",
  components: {
    Header,
    Todos
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Buy gifts",
          completed: true
        },
        {
          id: 2,
          title: "Bake cookies",
          completed: false
        },
        {
          id: 3,
          title: "Decorate house",
          completed: false
        },
        {
          id: 4,
          title: "Sent invitations",
          completed: false
        },
      ]
    }
  },
  methods: {
    deleteTodo(todoId) {
      this.todos = this.todos.filter(todo => todoId !== todo.id)
    }
  }
}
</script>


<style>
  * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

  body {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
  
</style>
