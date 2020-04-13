<template>
  <b-container>
    <h2>Todo List</h2>
    <hr />
    <AddForm v-on:add-todo="addTodo" class="mb-2"/>
    <b-form-select v-model="selected" :options="options" class="mb-2"></b-form-select>
    <b-spinner label="Spinning" v-if="loading"></b-spinner>
    <TodoList v-else-if="filteredTodos.length" v-bind:todos="filteredTodos" @removeItem="removeItem" />
    <p v-else class="mt-2">Нет дел!</p>
  </b-container>
</template>

<script>
import TodoList from "@/components/TodoList";
import AddForm from "@/components/AddForm";
export default {
  name: "App",
  data() {
    return {
      todos: [],
      loading: true,
      selected: 'all',
      options: [
        { value: "all", text: "Все" },
        { value: "completed", text: "Выполненные" },
        { value: "non-completed", text: "Не выполненные" },
      ]
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=3")
      .then(response => response.json())
      .then(json => {
        this.todos = json;
        this.loading = false;
      });
  },
  computed: {
    filteredTodos() {
      if (this.selected === 'all') {
        return this.todos
      }
      if (this.selected === 'completed') {
        return this.todos.filter(t => t.completed)
      }
      if (this.selected === 'non-completed') {
        return this.todos.filter(t => !t.completed)
      }
    }
  },
  methods: {
    removeItem(id) {
      this.todos = this.todos.filter(item => item.id !== id);
    },
    addTodo(item) {
      this.todos.push(item);
    }
  },
  components: {
    TodoList,
    AddForm
  }
};
</script>
