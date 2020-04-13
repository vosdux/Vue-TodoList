<template>
  <b-list-group-item class="d-flex justify-content-between align-items-center" variant="{danger: todo.compteled}">
    <b-form-checkbox v-model="todo.completed">
      <span v-bind:class="{done: todo.completed}">
        <strong>{{todo.id}}</strong>
        {{todo.title | uppercase}}
      </span>
    </b-form-checkbox>
    <b-icon-x-circle-fill class="red" v-on:click="$emit('removeItem', todo.id)"></b-icon-x-circle-fill>
  </b-list-group-item>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  filters: {
    uppercase(value) {
      return value.toUpperCase();
    }
  }
};
</script>

<style scoped>

.red {
  color: red;
  cursor: pointer;
}

.done {
  text-decoration: line-through;
}

</style>