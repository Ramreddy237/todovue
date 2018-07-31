<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>title</label>
            <input v-model="todo_name" type='text'>
          </div>
          <div class='field'>
            <label>description</label>
            <input v-model="todo_description" type='text'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
              Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CreateTodo",
  props: {
    msg: String
  },
  data() {
    return {
      todo_name: "",
      todo_description: "",
      isCreating: true,
      done:false
    };
  },
  methods: {
    openForm() {
      this.isCreating = true;
    },
    closeForm() {
      this.isCreating = false;
    },
    sendForm() {
      if (this.todo_name.length > 0 && this.todo_description.length > 0) {
        const todo_name = this.todo_name;
        const todo_description = this.todo_description;
        this.$emit("create-todo", {
          todo_name,
          todo_description,
          done: false
        });
        this.todo_name = "";
        this.done=false
        this.todo_description = "";
        this.isCreating = false;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
