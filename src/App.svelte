<script>
	import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import AddPlayer from './AddPlayer.svelte';

	let players = [{
		name: "Giovanni",
		points: 41,
	}];

	function addPlayer(e) {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	}

	function deletePlayer(e) {
		players = players.filter(player => player.name !== e.detail)
	}
</script>

<Navbar/>
<main>
	<div class="container">
		<AddPlayer on:addplayer={addPlayer}/>
		{#if players.length === 0}
		<p class="has-text-center is-size-2">No players</p>
		{:else}
		{#each players as player }
			<Player name={player.name} points={player.points} on:delete={deletePlayer}/>
		{/each}
		{/if}
	</div>
</main>

<hr>
<footer class="footer">
	<div class="content has-text-centered">
	  <p>
		<strong>Simple Player Scoreboard</strong> by <a href="https://github.com/gionneves">Giovanni Neves Sadauscas</a> <br>
		project made with <a href="https://svelte.dev/">Svelte</a> and <a href="https://bulma.io/">Bulma</a>.
	  </p>
	</div>
  </footer>