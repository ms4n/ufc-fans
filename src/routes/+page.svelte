<script>
	import { onMount } from 'svelte';

	let data = [];
	onMount(async () => {
		const res = await fetch('https://ufc-fans-api.azurewebsites.net/upcoming-events');

		const results = await res.json();
		data = results;
		console.log(results);
	});
</script>

<main class="bg-gray-200 h-full ">
	<div class="container m-auto py-10">
		<h1 href="/" class="text-4xl font-bold "><a class="text-ufc-red" href="/">UFC </a>Fans</h1>

		{#each data as item}
			<div class="rounded-lg shadow bg-gray-300 p-10 mt-48 relative">
				<img src={item.fighter_1} alt="" class="h-80 absolute bottom-0 left-0" />
				<div class="text-center">
					<p class="text-3xl font-semibold text-ufc-red">{item.name}</p>
					<p class="text-gray-600 my-2">{item.date}</p>
					<p class="text-lg">{item.venue}</p>
				</div>
				<img src={item.fighter_2} alt="" class="h-80 absolute bottom-0 right-0 -scale-x-100" />
			</div>
		{/each}
	</div>
</main>
