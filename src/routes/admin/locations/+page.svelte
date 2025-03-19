<script>
	import { enhance } from '$app/forms';
	import Warning from '$lib/components/Warning.svelte';
	import { slide } from 'svelte/transition';
	let { data, form } = $props();
</script>

<div class="p-6 bg-white rounded-lg shadow-md">
	<div class="container text-center mb-6">
		<h1 class="text-2xl font-bold text-gray-800">Locations</h1>
		<a href="/admin/locations/new" class="text-blue-600 hover:underline">Write a new location</a>
	</div>

	<div class="space-y-4">
		{#if form && !form.success}
			<Warning message={form.message} />
		{/if}

		{#each data.locations as locations (locations.id)}
			<div
				class="p-4 bg-gray-100 rounded-md shadow-sm flex justify-between items-center"
				transition:slide
			>
				<p class="text-gray-700">{locations.id} - {locations.name}</p>
				<form action="?/deleteLocation" method="POST" use:enhance class="ml-4">
					<input type="hidden" name="id" value={locations.id} />
					<button
						type="submit"
						class="bg-red-600 hover:bg-red-700 text-white font-bold py-1 px-3 rounded-md shadow-sm"
						>Delete</button
					>
				</form>
			</div>
		{/each}
	</div>
</div>
