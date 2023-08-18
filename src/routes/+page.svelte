<script lang="ts">
	import '../global.css';
	import { userState } from '../shared-state';
	import Toolbar from './components/Toolbar.svelte';
</script>

<Toolbar />
{JSON.stringify($userState)}
