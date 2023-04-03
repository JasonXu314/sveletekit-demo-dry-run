<script lang="ts">
	import Button from '@smui/button';
	import Textfield from '@smui/textfield';
	import Todo from './Todo.svelte';

	let todoText: string = '';
	let todos: { text: string; completed: boolean }[] = [];
</script>

<Textfield type="text" label="Todo Text" bind:value={todoText} />
<Button
	on:click={() => {
		todos = [...todos, { text: todoText, completed: false }];
		todoText = '';
	}}
	variant="raised"
>
	Add Todo
</Button>

{#each todos as todo}
	<Todo bind:todo on:delete={() => (todos = todos.filter((t) => t !== todo))} />
{/each}
