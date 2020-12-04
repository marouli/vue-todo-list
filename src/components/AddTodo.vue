<template>
  <div>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="Submit" class="btn">
    </form>
  </div>
</template>

<script>
// import uuid from 'uuid';
export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);
      this.title = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
    width: 50%;
    height: 50px;
    margin: 40px auto;
  }
  input[type="text"] {
    flex: 10;
    padding: 16px;
    font-size: 14px;
  }
  input[type="submit"] {
    flex: 2;
    font-size: 14px;
  }
</style>