<template>
  <section class="todo-list">
    <h3>Pendientes</h3>
    <div class="list" id="todo-list">
      <div v-for="todo in todos_asc" :class="`todo-item ${todo.done && 'done'}`">
        <label>
          <input type="checkbox" v-model="todo.done" />
          <span :class="`bubble ${todo.category == 'business' ? 'business' : 'personal'}`"></span>
        </label>

        <div class="todo-content">
          <input type="text" v-model="todo.content" />
        </div>

        <div class="actions">
          <button class="delete" @click="removeTodo(todo)">Eliminar</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: ['todos_asc'],
  methods: {
    removeTodo(todo) {
      this.$emit('remove-todo', todo);
    },
  },
};
</script>

<style scoped>
/* Agrega tus estilos CSS aquí si es necesario */
</style>