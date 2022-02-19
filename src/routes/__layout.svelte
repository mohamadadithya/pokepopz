<script>
	import Nav from '../components/Nav.svelte';
</script>

<Nav />
<div class="p-8 max-w-6xl mx-auto font-poppins">
	<slot />
</div>

<style>
	@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap');

	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>
