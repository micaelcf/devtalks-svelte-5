<script lang="ts">
	import { fly } from 'svelte/transition';

	interface Props {
		count?: number;
	}

	let { count = $bindable(0) }: Props = $props();
</script>

{#key count}
	<div
		in:fly={{ y: -80, x: 0 }}
		out:fly={{ y: 80, x: 0 }}
		class="absolute bottom-32 rounded-lg border border-slate-100 bg-slate-300 p-3 text-lg shadow-xl"
	>
		{count}
	</div>
{/key}
