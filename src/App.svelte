<script>
	import Nasa from './lib/Nasa.svelte'	
	export let name;
	let count = 0;

	$: doble = count *2;
	$: quad = doble *2;

	function handleClick(){
		count++;
	}
</script>

<main>
	<h1>¡Hola {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<button on:click={handleClick}>
		Clicked {count} {count === 1 ? 'time' : 'times'}
	</button>
	<p>{count} * 2 = {doble}</p>
	<p>{doble} * 2 = {quad}</p>
	<Nasa />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>