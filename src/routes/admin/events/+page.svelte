<script>
	import { enhance } from '$app/forms';
	import { slide } from 'svelte/transition';
	import event from '$lib/assets/event.jpg';
	let { data } = $props();
</script>
<div class="p-6 bg-white rounded-lg shadow-md">
    <div class="mb-6">
        <img src={event} alt="event.jpg" class="w-full h-64 object-cover rounded-md shadow-md">
    </div>

    <div class="text-center mb-6">
        <h1 class="text-2xl font-bold text-gray-800">Today's Events</h1>
        <a href="/admin/events/new" class="text-blue-600 hover:underline">Create a new event</a>
    </div>

    <div class="space-y-4">
        {#each data.events as event (event.id)}
            <div class="p-4 bg-gray-100 rounded-md shadow-sm" transition:slide>
                <div class="mb-4">
                    <p class="text-gray-700 font-medium">ID: {event.id}</p>
                    <p class="text-gray-700 font-medium">TITLE: {event.title}</p>
                    <p class="text-gray-700 font-medium">LOCATION: {event.locationName}</p>
                    <p class="text-gray-700 font-medium">START DATE: {event.start_date}</p>
                </div>
                <form action="?/deleteEvent" method="POST" use:enhance class="text-right">
                    <input type="hidden" name="id" value={event.id} />
                    <button type="submit" class="bg-red-600 hover:bg-red-700 text-white font-bold py-1 px-3 rounded-md shadow-sm">Delete</button>
                </form>
            </div>
        {/each}
    </div>
</div>
