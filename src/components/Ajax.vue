<template>
	<div>
		<h1>Todos</h1>
		<ul>
			<li v-for="todo in todos" :key="todo.id" style="white-space: nowrap;">
				{{ todo.id }} - {{ todo.title }} - {{ todo.completed }}
			</li>
		</ul>
	</div>
</template>

<script>
	import axios from 'axios';

	export default {
		data() {
			return {
				todos: []
			};
		},
		mounted() {
			axios.get('https://jsonplaceholder.typicode.com/todos/')
			.then(response => {
				this.todos = response.data;
			})
			.catch(error => {
				console.error('Error when fething data: ', error);
			});
		}
	};
</script>
