<template>
    <b-list-group>
      <TodoItem
        v-for="todo of todos"
        v-bind:todo="todo"
        v-bind:key="todo.id"
        v-on:removeItem="removeItem"
      />
    </b-list-group>
</template>

<script>
import TodoItem from "@/components/TodoItem";
export default {
  props: ["todos"],
  components: {
    TodoItem
  },
  methods: {
    removeItem(id) {
      this.$emit("removeItem", id);
    }
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
</style>