<script>
	import Todo from './Todo.svelte';
	import AddTodo from './AddTodo.svelte';
	let newIndex = 0;
	let todos = [{
		description: 'Cook dinner',
		index: newIndex++
	}, {
		description: 'Take out trash',
		index: newIndex++
	}];

	const deleteTodo = (event) => {
		todos = todos.filter(todo => todo.index !== event.detail.index);
	};

	const addTodo = (event) => {
		const newTodo = {
			description: event.detail.description,
			index: newIndex++
		};
		todos = [...todos, newTodo];
	};
</script>

<style>
	.todos {
		border: solid 2px grey;
	}
</style>

<h1>My todo list:</h1>
<div class="todos">
	{#if todos.length === 0}
		<div>There is nothing to do!</div>
	{:else}
		{#each todos as todo (todo.index)}
			<Todo description={todo.description}
						index={todo.index}
						on:deleteClicked={deleteTodo} />
		{/each}
	{/if}
</div>
<AddTodo on:addTodo={addTodo} />