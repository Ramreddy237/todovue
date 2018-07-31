<template>
  <div id="app">
    <img src="./assets/logo.png">
          <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:create-todo="createTodo"></create-todo>
  </div>
</template>

<script>
import CreateTodo from './components/HelloWorld.vue'
import TodoList from './components/TodoList';
export default {
  name: 'app',
  components: {
    CreateTodo,
    TodoList
  },
  data() {
    return {
      todos: [{
        todo_name: 'Todo A',
        todo_description: 'Project A',
        done: false,
      }, {
        todo_name: 'Todo B',
        todo_description: 'Project B',
        done: true,
      }, {
        todo_name: 'Todo C',
        todo_description: 'Project C',
        done: false,
      }, {
        todo_name: 'Todo D',
        todo_description: 'Project D',
        done: false,
      }],
    };
  },
    methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
     alert('sucessfuly created TODO');
    },
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
