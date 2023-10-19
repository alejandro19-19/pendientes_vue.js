<template>
	<main class="app">
	  <Greeting :name="name" />
  
	  <CreateTodo :input_content="input_content" :input_category="input_category" @add-todo="addTodo" />
  
	  <TodoList :todos_asc="todos_asc" @remove-todo="removeTodo" />
	</main>
  </template>
  
  <script>
  import Greeting from '../components/Greeting.vue';
  import CreateTodo from '../components/CreateTodo.vue';
  import TodoList from '../components/TodoList.vue';
  
  export default {
	components: {
	  Greeting,
	  CreateTodo,
	  TodoList,
	},
	data() {
	  return {
		todos: [],
		name: '',
		input_content: '',
		input_category: null,
	  };
	},
	methods: {
	  addTodo(newTodoData) {
		const newTodo = {
		  content: newTodoData.content,
		  category: newTodoData.category,
		  done: false,
		  editable: true,
		  createdAt: new Date().getTime(),
		};
  
		this.todos.push(newTodo);
	  },
	  removeTodo(todo) {
		this.todos = this.todos.filter((t) => t !== todo);
	  },
	},
	computed: {
	  todos_asc() {
		return this.todos.sort((a, b) => a.createdAt - b.createdAt);
	  },
	},
  };
  </script>
