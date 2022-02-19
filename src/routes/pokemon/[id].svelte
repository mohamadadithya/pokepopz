<script context="module">
	export async function load({ params }) {
		const id = params.id;
		const url = `https://pokeapi.co/api/v2/pokemon/${id}/`;
		const res = await fetch(url);
		const poke = await res.json();
		return { props: { poke } };
	}
</script>

<script>
	export let poke;
	const type = poke.types[0].type.name;
</script>

<svelte:head>
	<title>{poke.name}</title>
</svelte:head>

<h1 class="capitalize text-4xl mb-2">{poke.name}</h1>
<p class="mb-4">
	Type: <strong class="capitalize">{type}</strong> | Height: <strong>{poke.height}</strong> |
	Weight:
	<strong>{poke.weight}</strong>
</p>
<img src={poke.sprites['front_default']} alt={poke.name} />
