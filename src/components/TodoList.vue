<template>
  <div>
    <div class="container">
      <div class="col-12">
        Vue Crash Course
      </div>
    </div>
    <div class="row">
      <p>Add Create Form</p>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <Todo
            v-for="(todo, index) in todos"
            :key="index"
            :todoString="todo.todoString"
            :completed="todo.completed"
            @on-delete="deleteTodo(todo)"
            @on-toggle="toggleTodo(todo)"
            @on-edit="editTodo(todo, $event)"
          ></Todo>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo";
export default {
  components: {
    Todo,
  },
  data() {
    return {
      todos: [
        { todoString: "Make Anglular Course", completed: true },
        { todoString: "Make Anglular Course", completed: true },
        { todoString: "Make React Course", completed: true },
        { todoString: "Make Youtube Videos", completed: true },
      ],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({
        todoString: newTodo,
        completed: false,
      });
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    editTodo(todo, newTodoString) {
      todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo) {
      this.todos = this.todos.filter((todo) => {
        return todo.todoString !== deleteTodo.todoString;
      });
    },
  },
};
</script>

<style></style>
