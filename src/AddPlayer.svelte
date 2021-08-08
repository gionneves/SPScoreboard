<script>
import { createEventDispatcher } from "svelte";


    const dispatch = createEventDispatcher();
   
    let player = {
        name:"",
        points: 0
    };

    function onSubmit(e) {
        e.preventDefault();
        dispatch("addplayer", player);
        player = {
            name:"",
            points: 0
        };
    };
</script>

<form on:submit={onSubmit} class="field is-grouped">
    <input class="input m-3" type="text" placeholder="Player Name" bind:value={player.name} required/>
    <input class="input m-3" type="number" placeholder="Player Points" bind:value={player.points}/>
    <input class="button is-primary m-3" type="submit" value="Add Player" />
</form>
    

