<script lang="ts">
	import { Add, Remove } from '@steeze-ui/material-design-icons';
	import { Icon } from '@steeze-ui/svelte-icon';

	interface Props {
		onIncrement?: () => void;
		onDecrement?: () => void;
	}

	let { onIncrement, onDecrement }: Props = $props();
</script>

<div class="flex items-center gap-2">
	<button
		class="rounded-lg border border-slate-100 bg-orange-400 p-3 shadow-lg active:shadow"
		onclick={onIncrement}
	>
		<Icon src={Add} theme="outline" class="size-6" />
	</button>
	<button
		class="rounded-lg border border-slate-100 bg-orange-400 p-3 shadow-lg active:shadow"
		onclick={onDecrement}
	>
		<Icon src={Remove} theme="outline" class="size-6" />
	</button>
</div>
