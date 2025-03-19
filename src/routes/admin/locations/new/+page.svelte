<script>
	import { enhance } from '$app/forms';
</script>

<div class="max-w-lg mx-auto bg-white p-6 rounded-lg shadow-md">
	<h1 class="text-2xl font-bold mb-4 text-gray-800">Create a New Location</h1>

	<form method="POST" action="?/createLocation" use:enhance class="space-y-4">
		<div>
			<label for="name" class="block text-sm font-medium text-gray-700">Name</label>
			<input
				type="text"
				id="name"
				name="name"
				placeholder="Enter location name"
				class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2"
			/>
		</div>

		<div>
			<label for="street" class="block text-sm font-medium text-gray-700">Street</label>
			<textarea
				id="street"
				name="street"
				placeholder="Enter street details"
				class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2 h-24"
			></textarea>
		</div>

		<button
			type="submit"
			class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-md shadow-sm transition-all"
		>
			Create Location
		</button>
	</form>
</div>
