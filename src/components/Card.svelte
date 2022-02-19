<script>
	import { fade } from 'svelte/transition';
	export let poke;
</script>

<a
	href={`/pokemon/${poke.id}`}
	class="p-8 bg-gray-200 text-gray-800 shadow-sm hover:shadow-md flex flex-col justify-center items-center rounded-md"
	transition:fade
>
	<img src={poke.image} alt={poke.name} />
	<h2 class="capitalize text-2xl">{poke.name}</h2>
</a>
