<script lang="ts">
	import type { Snippet } from 'svelte';

	type Props = {
		children: Snippet;
		class?: string;
	};

	let { children, class: klass = '' }: Props = $props();
</script>

<h1 class="text-3xl font-semibold text-orange-500 {klass}">
	{@render children()}
</h1>
