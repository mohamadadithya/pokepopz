<script context="module">
	export async function load({ params }) {
		const url = `https://pokeapi.co/api/v2/pokemon?limit=60`;
		const res = await fetch(url);
		const data = await res.json();
		const loadedPokemon = data.results.map((data, index) => {
			return {
				name: data.name,
				id: index + 1,
				image: `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${
					index + 1
				}.png`
			};
		});
		return { props: { pokemon: loadedPokemon } };
	}
</script>

<script>
	import Card from '../components/Card.svelte';
	export let pokemon;

	let searchKeyword = '';
	let filteredPokemon = [];

	$: {
		if (searchKeyword) {
			// Search the pokemon
			filteredPokemon = pokemon.filter((poke) =>
				poke.name.toLowerCase().includes(searchKeyword.toLowerCase())
			);
		} else {
			filteredPokemon = [...pokemon];
		}
	}
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<h1 class="text-4xl text-center my-6 uppercase font-bold tracking-widest">Pokepopz</h1>

<input
	class="w-full rounded-md text-lg p-2 border-2 border-gray-200 focus:border-gray-400 outline-none"
	type="text"
	name="search"
	id="search"
	placeholder="Search Pokemon"
	autocomplete="off"
	bind:value={searchKeyword}
/>

<div class="grid gap-4 md:grid-cols-2 grid-cols-1 py-4">
	{#each filteredPokemon as poke}
		<Card {poke} />
	{/each}
</div>
