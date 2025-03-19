<script>
	import { enhance } from '$app/forms';
	import Warning from '$lib/components/Warning.svelte';
	import { slide } from 'svelte/transition';
	let { data, form } = $props();
</script>

<div class="flex flex-col items-center min-h-screen bg-gray-100 p-6">
	<div class="bg-white shadow-lg rounded-lg p-6 w-full max-w-md mb-6">
		<h1 class="text-2xl font-bold text-gray-800 mb-4">Write a new Categorie</h1>

		<form method="POST" action="?/createCategorie" use:enhance>
			<label for="name" class="block text-gray-700">Name</label>
			<textarea
				placeholder="Name"
				name="name"
				class="w-full p-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500 mb-4"
			></textarea>

			<button
				type="submit"
				class="w-full bg-purple-500 text-white py-2 rounded-lg hover:bg-purple-600"
				>Create Categorie</button
			>
		</form>
	</div>

	<div class="bg-white shadow-lg rounded-lg p-6 w-full max-w-2xl">
		<h1 class="text-2xl font-bold text-gray-800 mb-4">Categories</h1>
		<a href="/admin/categories/new" class="text-blue-500 hover:underline">Write a new categorie</a>

		{#if form && !form.success}
			<Warning message={form.message} />
		{/if}

		<div class="mt-4 space-y-4">
			{#each data.categories as categorie (categorie.id)}
				<div
					class="flex justify-between items-center p-4 bg-gray-100 rounded-lg shadow-md transition-transform transform hover:scale-105"
				>
					<p class="text-gray-700">{categorie.id} - {categorie.name}</p>
					<form action="?/deleteCategorie" method="POST" use:enhance>
						<input type="hidden" name="id" value={categorie.id} />
						<button
							type="submit"
							class="bg-red-500 text-white py-1 px-3 rounded-lg hover:bg-red-600">Delete</button
						>
					</form>
				</div>
			{/each}
		</div>
	</div>
</div>
