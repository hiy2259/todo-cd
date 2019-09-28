<template>
  <div>
      <ul>
          <li v-for="(todoItem, index) in items" v-bind:key="index">
              {{todoItem}}
              <button @click="removeTodoItem(todoItem, index)">remove</button>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
	props: ['items'],
	methods: {
		removeTodoItem(todoItem, index) {
			this.$emit('remove', todoItem, index);
		},
	},
};
</script>

<style>
</style>