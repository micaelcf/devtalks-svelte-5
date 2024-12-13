<script lang="ts">
	import { page } from '$app/stores';
	import Title from '$lib/components/Title.svelte';
	import { ArrowLeft, ArrowRight } from '@steeze-ui/material-design-icons';
	import '../app.css';
	import Button from '$lib/components/Button.svelte';

	const exemplos = [
		{
			label: 'Runas',
			link: '/runas'
		},
		{
			label: 'Snippets',
			link: '/snippets'
		},
		{
			label: 'Eventos',
			link: '/eventos'
		},
		{
			label: 'Componente no padrão Svelte 5',
			link: '/componente'
		}
	];

	let { children } = $props();

	let currentExemploIndex = $derived(
		exemplos.findIndex((exemplo) => exemplo.link === $page.url.pathname)
	);

	$inspect(currentExemploIndex, currentExemploIndex > 0);
</script>

<main class="h-[100svh] w-[100svw] bg-slate-50 text-slate-600">
	<section class="flex h-full w-full flex-col items-center justify-center">
		<Title class="pt-4 text-4xl">Exemplos</Title>
		<h2 class="text-2xl">{exemplos[currentExemploIndex]?.label}</h2>
		<div class="mt-4 flex h-full w-[90%] items-center justify-center">
			<Button
				as="a"
				icon={ArrowLeft}
				disabled={currentExemploIndex < 0}
				href={currentExemploIndex > 0 ? exemplos[currentExemploIndex - 1]?.link : '/'}
			></Button>
			<section class="flex h-full w-full items-center justify-center">{@render children()}</section>
			<Button
				as="a"
				icon={ArrowRight}
				disabled={currentExemploIndex < 0}
				href={currentExemploIndex < exemplos.length ? exemplos[currentExemploIndex + 1]?.link : '/'}
			></Button>
		</div>
	</section>
</main>
