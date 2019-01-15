<template>
  <div id="app">
    <div class="container">
      <Header/>
      <AddTodo v-on:add-todo="addTodo"/>
      <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
    </div>
  </div>
</template>

<script>
import Todos from "./components/Todos";
import Header from "./components/Header";
import AddTodo from "./components/AddTodo";
import uuid from "uuid";

export default {
  name: "app",
  components: {
    Header,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [
        {
          id: uuid.v4(),
          title: "Learn Vue",
          completed: false
        },
        {
          id: uuid.v4(),
          title: "Learn React",
          completed: false
        },
        {
          id: uuid.v4(),
          title: "Learn Angular",
          completed: false
        }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.container {
  padding: 5vw 15vw;
}

@media only screen and (max-width: 768px) {
  .container {
    padding: 0 5px;
  }
}
</style>
