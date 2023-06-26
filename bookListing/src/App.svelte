<script> 
    import Card from './components/Card.svelte';

    import Outer from './components/Outer.svelte';

    import Popup from './components/Popup.svelte';

	import {fade} from 'svelte/transition';

	function handleCard(event){
		event.detail;
	}

	function handleGreet(event){
		alert(event.detail);
	}

	let showPopup = false;

	let books = ['Learning Svelte', 'The Zen of Cooking Tea'];
	let newBook = '';

	function addBook (evt){
		if(evt.key === 'Enter'){
			books = [...books, newBook];
			newBook = ' ';
		}
	}

	let favoriteSpiceGirl = [];

	const formValues = {
		remoteWork: false
	}
</script>

<main>
	<label>
		<h3>Add Book</h3>
		<input type="text" bind:value = {newBook} on:keydown={addBook}>
	</label>

	<h3>My Books</h3>
	<ul>
		{#each books as book (book)}
		  <li transition:fade>{book}</li>
		{/each}
	</ul>

	<Card on:changeColor = {handleCard}/>
     
	<Outer on:greet = {handleGreet}/>

	<button on:click={() => (showPopup = true)}>SHOW POPUP</button>
    {#if showPopup}
	<Popup on:close={() => (showPopup = false)}/>
	{/if}

<h3>Who is your favorite Spice Girl</h3>
<label for="scary">Scary</label>
<input bind:group={favoriteSpiceGirl} type="checkbox" id="scary" value="scary">
<label for="posh">Posh</label>
<input bind:group={favoriteSpiceGirl} type="checkbox" id="Posh" value="Posh">
<label for="baby">Baby</label>
<input bind:group={favoriteSpiceGirl} type="checkbox" id="baby" value="baby">
<label for="sporty">Sporty</label>
<input bind:group={favoriteSpiceGirl} type="checkbox" id="sporty" value="sporty">
<h3>Answer: {favoriteSpiceGirl}</h3>

<div>
	<input type="checkbox" id="remoteWork" bind:checked={formValues.remoteWork}>
	<label for="remoteWork">Open to Remote Work?</label>
</div>

</main>

<style>
	*{
		margin: 0;
		padding: 0;
		box-sizing: border-box;
		overflow-y: hidden;
	}
	main {
		text-align: center;
		padding: 7em;
		min-height: 100vh;
		max-width: 100%;
		margin: 0 auto;
        background: linear-gradient(rgb(38, 69, 62), rgb(232, 252, 201));
	}

button {
    background-color: #425b1d; /* Green */
    border: none;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
  }
	h3 {
		color: #111f21;
		text-transform: uppercase;
		font-size: 1.4em;
		font-weight: 100;
	}

	input + label {
		padding: 15px 15px;
		display: inline-flex;
	}

	li {
		list-style: none;
		color: rgb(34, 34, 34);
		font-size: 1.3em;
		font-weight: 100;
	}

	ul {
		padding: 5px 0;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>