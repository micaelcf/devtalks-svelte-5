<script lang="ts">
	import Title from '$lib/components/Title.svelte';
	import { ChevronRight } from '@steeze-ui/material-design-icons';
	import { Icon } from '@steeze-ui/svelte-icon';
</script>

{#snippet link({ label, link }: { label: string; link: string })}
	<a href={link} class="transition-all duration-300 hover:text-orange-500">
		<Icon src={ChevronRight} class="size-6"></Icon>
		{label}
	</a>
{/snippet}

<div class="flex h-full w-[80%] flex-col items-center justify-center">
	<div class="flex flex-col items-center">
		<Title>Vamos começar a diversão!!!!</Title>
		<h1 class="text-lg font-semibold">Exemplos que vocês verão hoje:</h1>
	</div>
	<ul class="mt-3 [&>li>a]:flex [&>li>a]:items-center [&>li>a]:gap-1">
		<li>
			{@render link({ label: 'Runas', link: '/runas' })}
		</li>
		<li>
			{@render link({ label: 'Snippets', link: '/snippets' })}
		</li>
		<li>
			{@render link({ label: 'Eventos', link: '/eventos' })}
		</li>
		<li>
			{@render link({ label: 'Componente no padrão Svelte 5', link: '/componente' })}
		</li>
	</ul>
</div>
