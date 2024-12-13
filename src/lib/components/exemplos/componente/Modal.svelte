<script lang="ts">
	import { Close } from '@steeze-ui/material-design-icons';
	import { Icon } from '@steeze-ui/svelte-icon';
	import type { Snippet } from 'svelte';
	import { sineIn, sineOut } from 'svelte/easing';
	import { fade, fly } from 'svelte/transition';

	interface Props {
		showCloseButton?: boolean;
		children?: Snippet;
		closeButton?: Snippet;
		open?: boolean;
		title?: Snippet;
		onClose?: () => void;
		onOpen?: () => void;
	}

	let {
		showCloseButton = true,
		open = $bindable(false),
		title,
		closeButton,
		children,
		onClose,
		onOpen
	}: Props = $props();

	const handleClose = () => {
		open = false;
		onClose?.();
	};

	$effect(() => {
		if (open) {
			onOpen?.();
		}
	});
</script>

{#if open}
	<div class="fixed inset-0 z-50 justify-end">
		<div
			class="fixed inset-0 z-auto h-full w-full bg-black/75"
			in:fade={{ duration: 300, easing: sineOut }}
			out:fade={{ duration: 200, easing: sineIn }}
		></div>
		<div class="fixed inset-0 flex flex-col items-center justify-end">
			<div
				in:fly={{ y: '100%' }}
				out:fly={{ duration: 200, easing: sineOut, y: '100%' }}
				class="[&>:not(header)]:max-w-screen-home w-full transform overflow-y-auto bg-white text-left
      align-middle text-slate-700 shadow-xl transition-all [&>:not(header)]:mx-auto [&>:not(header)]:w-full"
			>
				<header class="border-b border-slate-200 px-3 pb-3 pt-8 text-orange-500">
					<h3 class="max-w-screen-home mx-auto w-full text-lg font-bold text-orange-500">
						{#if title}
							{@render title()}
						{:else}
							Titulo do modal
						{/if}
						{#if showCloseButton}
							{#if closeButton}
								{@render closeButton()}
							{:else}
								<button
									class="absolute right-5 top-5 inline-flex flex-none text-slate-500 focus:outline-none"
									title="Fechar"
									onclick={handleClose}
								>
									<Icon src={Close} class="h-auto w-6" />
								</button>
							{/if}
						{/if}
					</h3>
				</header>
				{@render children?.()}
			</div>
		</div>
	</div>
{/if}
