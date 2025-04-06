<script>
	import { flip } from 'svelte/animate';
	let { data } = $props();
	let filteredEvents = $state(data.events);
	let selectedCategorie = $state('all');

	function filterEvents() {
		if (selectedCategorie === 'all') {
			filteredEvents = data.events;
		} else {
			filteredEvents = data.events.filter((e) => e.category_id === selectedCategorie.id);
		}
	}
</script>

<div class="p-6 bg-gray-100 min-h-screen">
	<div class="max-w-md mx-auto bg-white shadow-lg rounded-lg p-6">
		{#if data.user}
			<p class="text-lg font-semibold text-gray-700">Welcome back, {data.user.username}</p>
			<form action="/logout?/logout" method="POST" class="mt-4">
				<button
					type="submit"
					class="w-full bg-blue-500 text-white py-2 rounded-lg hover:bg-blue-600">Logout</button
				>
			</form>
			<form action="/logout?/deleteAccount" method="POST" class="mt-2">
				<button type="submit" class="w-full bg-red-500 text-white py-2 rounded-lg hover:bg-red-600"
					>Delete Account</button
				>
			</form>
		{:else}
			<p class="text-gray-600">You are not logged in.</p>
			<p class="mt-4">
				<a href="/login" class="text-blue-500 hover:underline">Login</a>
				or
				<a href="/register" class="text-blue-500 hover:underline">Register</a>
			</p>
		{/if}
	</div>

	<div class="mt-8 max-w-2xl mx-auto bg-white shadow-lg rounded-lg p-6">
		<h1 class="text-2xl font-bold text-gray-800">My Event App</h1>
		<p class="text-gray-600 mt-2">Here are the current events.</p>

		<select
			id="category"
			bind:value={selectedCategorie}
			onchange={filterEvents}
			class="mt-4 w-full border-gray-300 rounded-lg p-2"
		>
			<option value="all">All</option>
			{#each data.categories as category}
				<option value={category}>{category.name}</option>
			{/each}
		</select>

		<div class="mt-4 space-y-2">
			{#each filteredEvents as event (event.id)}
			<img src={event.image_url} alt="" class="w-120 h-auto rounded-lg shadow-md" />			     
				<p class="p-2 bg-gray-100 rounded-lg">
					{event.id} - {event.title} - {new Date(event.start_date).toDateString()}
				</p>
			{/each}
		</div>
	</div>
</div>
