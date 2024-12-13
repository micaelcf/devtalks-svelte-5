<script lang="ts">
	import { Icon, type IconSource } from '@steeze-ui/svelte-icon';
	import type { Snippet } from 'svelte';
	import type { HTMLButtonAttributes } from 'svelte/elements';

	interface Props extends HTMLButtonAttributes {
		icon?: IconSource;
		children?: Snippet;
		as?: 'a' | 'button';
		href?: string;
	}

	let { as = 'button', icon, href, children, ...restProps }: Props = $props();
</script>

<svelte:element
	this={as}
	{...restProps}
	{href}
	class="flex items-center gap-1.5 rounded-full border border-slate-100 p-2 shadow-lg
	transition-all duration-300 active:scale-95 active:shadow-sm disabled:cursor-not-allowed
	disabled:opacity-80 disabled:shadow-none {restProps.class}"
>
	{#if icon}
		<Icon src={icon} theme="outline" class="h-9 w-9" />
	{/if}
	{@render children?.()}
</svelte:element>
