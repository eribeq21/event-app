<script>
	import { enhance } from '$app/forms';
	let { data } = $props();
</script>

<div class="flex justify-center items-center min-h-screen bg-gray-100">
	<div class="bg-white shadow-lg rounded-lg p-6 w-full max-w-md">
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
</div>
