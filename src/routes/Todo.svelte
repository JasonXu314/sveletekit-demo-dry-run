<script lang="ts">
	import Card, { Content } from '@smui/card';
	import Actions from '@smui/card/src/Actions.svelte';
	import Checkbox from '@smui/checkbox';
	import FormField from '@smui/form-field';
	import IconButton from '@smui/icon-button';
	import { createEventDispatcher } from 'svelte';

	export let todo: { text: string; completed: boolean };

	const dispatch = createEventDispatcher<{ delete: void }>();
</script>

<Card padded>
	<Content style="color: {todo.completed ? 'green' : 'unset'}">{todo.text}</Content>
	<Actions>
		<IconButton on:click={() => dispatch('delete')} class="material-icons">delete</IconButton>
		<FormField>
			<Checkbox bind:checked={todo.completed} />
			<span slot="label">Completed</span>
		</FormField>
	</Actions>
</Card>
