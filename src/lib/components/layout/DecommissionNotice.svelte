<script lang="ts">
	import { onMount } from 'svelte';

	const storageKey = 'mcgpt-decommission-notice-dismissed';
	let dismissed = false;

	onMount(() => {
		dismissed = localStorage.getItem(storageKey) === 'true';
	});

	const dismiss = () => {
		localStorage.setItem(storageKey, 'true');
		dismissed = true;
	};
</script>

{#if !dismissed}
	<div
		class="fixed inset-x-0 top-0 z-[100] flex items-center justify-center gap-3 border-b border-amber-300 bg-amber-100 px-4 py-2 text-center text-sm font-semibold text-amber-950 shadow-md dark:border-amber-500/50 dark:bg-amber-950 dark:text-amber-100"
		role="alert"
	>
		<span>mcGPT verrà dismesso a fine agosto. Salva eventuali conversazioni importanti prima di quella data.</span>
		<button
			class="shrink-0 rounded p-1 text-lg leading-none hover:bg-amber-200 dark:hover:bg-amber-900"
			aria-label="Chiudi avviso"
			on:click={dismiss}>&times;</button
		>
	</div>
{/if}
