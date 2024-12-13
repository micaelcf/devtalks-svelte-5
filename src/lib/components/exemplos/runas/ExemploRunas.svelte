<script lang="ts">
	import { Add, Remove } from '@steeze-ui/material-design-icons';
	import { Icon } from '@steeze-ui/svelte-icon';
	import { fly } from 'svelte/transition';

	let count = $state(0);
</script>

<div class="relative flex flex-col items-center gap-4">
	<div class="flex items-center gap-2">
		<button
			onclick={() => count++}
			class="rounded-lg border border-slate-100 bg-orange-400 p-3 shadow-lg active:shadow"
		>
			<Icon src={Add} theme="outline" class="size-6" />
		</button>
		<button
			onclick={() => count--}
			class="rounded-lg border border-slate-100 bg-orange-400 p-3 shadow-lg active:shadow"
		>
			<Icon src={Remove} theme="outline" class="size-6" />
		</button>
	</div>
	{#key count}
		<div
			in:fly={{ y: -80, x: 0 }}
			out:fly={{ y: 80, x: 0 }}
			class="absolute bottom-32 rounded-lg border border-slate-100 bg-slate-300 p-3 text-lg shadow-xl"
		>
			{count}
		</div>
	{/key}
</div>
