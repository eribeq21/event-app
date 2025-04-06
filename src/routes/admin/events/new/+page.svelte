<script>
	import { enhance } from '$app/forms';
	let { data } = $props();
</script>
<div class="max-w-lg mx-auto bg-white p-6 rounded-lg shadow-md">
    <h1 class="text-2xl font-bold mb-4 text-gray-800">Create a new event</h1>

    <form method="POST" action="?/createEvent" use:enhance class="space-y-4" enctype="multipart/form-data">
        <div>
            <label for="title" class="block text-sm font-medium text-gray-700">Title</label>
            <input type="text" placeholder="Title" name="title"
                class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2">
        </div>
        <div>
            <label for="image" class="block text-sm font-medium text-gray-700">Image</label>
            <input
				type="file"
				name="image"
				class="block w-full cursor-pointer rounded-lg border border-gray-300 bg-white px-4 py-2 text-gray-700 shadow-sm"
			/>
        </div>

        <div>
            <label for="description" class="block text-sm font-medium text-gray-700">Description</label>
            <textarea placeholder="Description" name="description"
                class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2 h-24"></textarea>
        </div>

        <div>
            <label for="url" class="block text-sm font-medium text-gray-700">URL</label>
            <input type="text" placeholder="URL" name="url"
                class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2">
        </div>

        <div class="grid grid-cols-2 gap-4">
            <div>
                <label for="startDate" class="block text-sm font-medium text-gray-700">Start Date</label>
                <input type="date" name="startDate"
                    class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2">
            </div>
            <div>
                <label for="endDate" class="block text-sm font-medium text-gray-700">End Date</label>
                <input type="date" name="endDate"
                    class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2">
            </div>
        </div>

        <div class="grid grid-cols-2 gap-4">
            <div>
                <label for="startTime" class="block text-sm font-medium text-gray-700">Start Time</label>
                <input type="time" name="startTime"
                    class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2">
            </div>
        </div>

        <div>
            <label for="location" class="block text-sm font-medium text-gray-700">Location</label>
            <select name="locationId"
                class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2">
                {#each data.locations as location (location.id)}
                    <option value={location.id}>{location.name}</option>
                {/each}
            </select>
        </div>

        <div>
            <label for="category" class="block text-sm font-medium text-gray-700">Category</label>
            <select name="categoryId"
                class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 p-2">
                {#each data.categories as categorie (categorie.id)}
                    <option value={categorie.id}>{categorie.name}</option>
                {/each}
            </select>
        </div>

        <button type="submit"
            class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-md shadow-sm transition-all">
            Create Event
        </button>
    </form>
</div>
<style>
	h1 {
		font-size: 32px;
		color: #2a2b55;
		text-align: center;
		margin-bottom: 24px;
		font-weight: 700;
	}

	form {
		max-width: 500px;
		margin: 0 auto;
		padding: 32px;
		background-color: #fff;
		border-radius: 8px;
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
		display: flex;
		flex-direction: column;
	}

	label {
		font-size: 16px;
		font-weight: 600;
		margin-bottom: 10px;
		color: #333;
		font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
		text-transform: uppercase;
	}

	input,
	textarea {
		padding: 12px;
		font-size: 16px;
		border: 1px solid #ddd;
		border-radius: 4px;
		margin-bottom: 16px;
	}

	textarea {
		min-height: 120px;
	}

	button {
		background-color: #0088a9;
		color: #fff;
		padding: 12px 20px;
		font-size: 16px;
		border: none;
		border-radius: 4px;
		cursor: pointer;
		transition: background-color 0.3s ease;
		font-weight: 600;
	}

	button:hover {
		background-color: #00788c;
	}

	select {
		margin-bottom: 10px;
		height: 50px;
		border: 1px solid rgba(73, 73, 73, 0.2);
		border-radius: 3px;
	}
</style>
