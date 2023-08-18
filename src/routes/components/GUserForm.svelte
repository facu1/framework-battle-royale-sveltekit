<script lang="ts">
	import GButton from '$lib/GButton.svelte';
	import { ButtonTypes } from '../../models';
	import { dialogState, emptyUserState, userState } from '../../shared-state';

	let formState = emptyUserState;

	const submit = (e: any) => {
		e.preventDefault();
		userState.set(formState);
		dialogState.set(false);
	};
</script>

<form class="form" on:submit={submit}>
	<label for="name">Name</label>
	<input type="text" name="name" id="name" bind:value={formState.name} />
	<GButton type={ButtonTypes.SUBMIT}>Save</GButton>
</form>

<style>
	.form {
		display: flex;
		flex-flow: row;
		gap: 1rem;
		align-items: center;
	}
</style>
