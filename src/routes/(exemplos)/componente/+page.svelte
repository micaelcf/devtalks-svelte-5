<script lang="ts">
	import Button from '$lib/components/Button.svelte';
	import Modal from '$lib/components/exemplos/componente/Modal.svelte';

	let modalOpen = $state(false);
</script>

<Button onclick={() => (modalOpen = true)} class="!p-4 font-semibold">Abrir modal</Button>

<Modal bind:open={modalOpen}>
	{#snippet title()}
		Titulo dancinha
	{/snippet}
	<div class="flex w-full items-center justify-center py-20">
		<img src="/animacao.gif" alt="animacao" />
	</div>
</Modal>
