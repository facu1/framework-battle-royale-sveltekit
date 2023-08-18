<script lang="ts">
	import GButton from '$lib/GButton.svelte';
	import GDialog from '$lib/GDialog.svelte';
	import { dialogState } from '../../shared-state';
	import GUserForm from './GUserForm.svelte';

	const openDialog = () => {
		dialogState.set(true);
	};
</script>

<div class="toolbar-container">
	<p>Framework Battle Royale: <strong>SvelteKit</strong></p>
	<GButton on:click={openDialog}>Open Dialog</GButton>
</div>
<GDialog>
	<GUserForm />
</GDialog>

<style>
	.toolbar-container {
		display: flex;
		gap: 1rem;
		background-color: var(--primary);
		color: var(--text-dark);
		padding: 1rem;
		max-height: 54px;
		align-items: center;
		justify-content: space-between;
	}
</style>
