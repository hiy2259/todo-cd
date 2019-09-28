<template>
  <div>
    <TodoHeader></TodoHeader>
    <TodoInput v-on:add="addTodoItem"></TodoInput>
    <TodoList v-bind:items="todoItems" v-on:remove="removeTodoItem"></TodoList>
    <TodoFooter v-on:clear="clearTodoItems"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader';
import TodoInput from './components/TodoInput';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter';

export default {
	components: {
		TodoHeader,
		TodoInput,
		TodoList,
		TodoFooter,
	},
	data: function() {
		return {
			todoItems: [],
		};
	},
	methods: {
		fetchTodoItems() {
			for (let i = 0, l = localStorage.length; i < l; i++) {
				let item = localStorage.key(i);
				if (item === 'loglevel:webpack-dev-server') {
					continue;
				}
				this.todoItems.push(item);
			}
		},
		addTodoItem(value) {
			this.todoItems.push(value);
			localStorage.setItem(value, value);
		},
		removeTodoItem(todoItem, index) {
      this.todoItems.splice(index, 1);
			localStorage.removeItem(todoItem);
    },
		clearTodoItems() {
			this.todoItems = [];
			localStorage.clear();
		},
	},
	created() {
		this.fetchTodoItems();
	},
};
</script>

<style>
</style>