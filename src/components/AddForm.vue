<template>
    <b-input-group prepend="Задача" class="mt-3">
      <b-form-input v-model="title"></b-form-input>
      <b-input-group-append>
        <b-button variant="outline-success" v-on:click="submitForm">Добавить</b-button>
      </b-input-group-append>
    </b-input-group>
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        submitForm() {
            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                };
                this.$emit('add-todo', newTodo)
            }
        }
    }
}
</script>

<style scoped>
form {
  display: flex;
}
input {
  width: 400px;
}
</style>