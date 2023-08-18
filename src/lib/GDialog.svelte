<script lang="ts">
	import { dialogState } from '../shared-state';
	import GButton from './GButton.svelte';

	$: isOpen = `${$dialogState ? ' open' : ''}`;

	const closeDialog = () => {
		dialogState.set(false);
	};
</script>

<div class={`dialog-background${isOpen}`}>
	<dialog open={$dialogState} class={`dialog-container${isOpen}`}>
		<slot />
		<GButton on:click={closeDialog}>Close</GButton>
	</dialog>
</div>

<style>
	.dialog-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.5);
		display: flex;
		align-items: center;
		justify-content: center;
		z-index: 9999;
		visibility: hidden;
		opacity: 0;
		pointer-events: none;
		transition: opacity 0.5s, visibility 0.5s;
	}

	.dialog-container {
		background-color: var(--primary-light);
		padding: 1rem;
		display: flex;
		flex-direction: column;
		gap: 1rem;
		border-radius: 1rem;
		transform: scale(0);
		transition: transform 0.5s, visibility 0.5s;
	}

	.dialog-background.open {
		visibility: visible;
		opacity: 1;
		pointer-events: auto;
	}

	.dialog-container.open {
		transform: scale(1);
	}
</style>
