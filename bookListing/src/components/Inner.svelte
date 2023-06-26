<script>
    import { createEventDispatcher  } from 'svelte';
    const dispatch = createEventDispatcher();

    function greet(){
        dispatch('greet', 'HELLO');
    }
</script>

<button on:click = {greet}>Greet</button>

<style>
button {
    background-color: #122c35; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
  }
</style>