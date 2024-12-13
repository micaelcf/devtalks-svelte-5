<script lang="ts">
	import Botoes from './Botoes.svelte';
	import DisplayNumero from './DisplayNumero.svelte';

	let count = $state(0);
</script>

<div class="relative flex flex-col items-center gap-4">
	<Botoes onIncrement={() => count++} onDecrement={() => count--} />
	<DisplayNumero bind:count></DisplayNumero>
</div>
