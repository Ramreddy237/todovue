<template>
  <div>
    <p class="tasks">Completed Todo: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p class="tasks">Pending Todos: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo"
  v-bind:key="index"
     v-on:complete-todo="completeTodo" v-for="(todo,index) in todos" :todo.sync="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >
import Todo from './Todo';
export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
 
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);

      }
    ,
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = true;
     alert('sucessfuly completed todo');
    },
  },
};
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>