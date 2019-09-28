<template>
  <div>
      <input type="text" v-model="inputText" @keyup.enter="addTodo">
      <button @click="addTodo">add</button>
  </div>
</template>

<script>
export default {
	data: function() {
		return {
			inputText: '',
		};
	},
	methods: {
		addTodo() {
			this.$emit('add', this.inputText);
			this.clearInput();
		},
		clearInput() {
			this.inputText = '';
		},
	},
};
</script>

<style>
</style>