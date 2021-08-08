<script>
import { createEventDispatcher } from "svelte";

	const dispath = createEventDispatcher();

    export let name;
    export let points;
	let showControls = false;

	const viewMore = () => {showControls = !showControls};

	function addP() {
		points += 1;
	}

	function remoP() {
		points -= 1;
	}

	function onDelete() {
		dispath("delete", name);
	}
</script>

<main>
	<div class="box my-3">		
		<div class="has-text-right">
			<div class="delete" on:click={onDelete}>...</div>
		</div>	
		<h1 class="is-size-1">
			{name} 
			<button class="has-text-right px-3" on:click={viewMore}> + </button>
		</h1>
		<h3 class="is-size-3 mb-4">{points}</h3>
		{#if showControls}
		<div class="is-grouped">
			<button class="button is-light mx-1" on:click={addP}> + </button>
			<button class="button is-dark mx-1" on:click={remoP}> - </button>
		</div>
		<div class="m-2">
			<input class="input" type="number" bind:value={points} />
		</div>
		
		{/if}
	</div>
</main>
