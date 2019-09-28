<template>
  <div>
    <button @click="clearAllItems">clear all</button>
  </div>
</template>

<script>
export default {
	methods: {
		clearAllItems() {
			this.$emit('clear');
		},
	},
};
</script>

<style>
</style>