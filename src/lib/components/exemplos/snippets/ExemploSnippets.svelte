<script lang="ts">
</script>

{#snippet textoSnippet(nome: string)}
	<p class="border border-slate-100 text-lg font-semibold">Esse texto é do {nome}!</p>
{/snippet}

<div class="flex flex-col items-center gap-4">
	<img src="/snippetsExemplo.png" alt="Exemplo de snippets" />
	{@render textoSnippet('Leozinho')}
	{@render textoSnippet('Jaguar')}
	{@render textoSnippet('Fofs')}
	{@render textoSnippet('Daniel')}
</div>
