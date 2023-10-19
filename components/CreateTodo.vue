<template>
  <section class="create-todo">
    <h3>Crear un pendiente</h3>

    <form id="new-todo-form" @submit.prevent="addTodo">
      <h4>¿Que hay en tu lista de pendientes?</h4>
      <input type="text" name="content" id="content" placeholder="e.j. Hacer la tarea " v-model="input_content" />

      <h4>Selecciona una categoria</h4>
      <div class="options">
        <label>
          <input
            type="radio"
            name="category"
            value="business"
            v-model="input_category"
          />
          <span class="bubble business"></span>
          <div>Trabajo</div>
        </label>

        <label>
          <input
            type="radio"
            name="category"
            value="personal"
            v-model="input_category"
          />
          <span class="bubble personal"></span>
          <div>Personal</div>
        </label>
      </div>

      <input type="submit" value="Añadir Pendiente" />
    </form>
  </section>
</template>

<script>
export default {
  props: ['input_content', 'input_category'],
  methods: {
    addTodo() {
      if (this.input_content.trim() === '' || this.input_category === null) {
        return;
      }

      this.$emit('add-todo', {
        content: this.input_content,
        category: this.input_category,
      });

    },
  },
};
</script>
