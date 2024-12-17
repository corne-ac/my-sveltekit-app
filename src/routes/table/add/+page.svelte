<script>
	import { goto } from '$app/navigation';
    import { supabase } from '$lib/supabaseClient';

    /** @type {{ data: import('./$types').PageData }} */
    let { data } = $props();

    let title = $state('');
    let description = $state('');
    let number = $state('');
    let date = $state('');
    let time = $state('');
    let message = $state('');
    let isSubmitting = $state(false); 

    const handleSubmit = async () => {
		isSubmitting = true;

        const { error } = await supabase
            .from('items')
            .insert([{ title, description, number, date, time }]);

        if (error) {
        console.error('Error inserting data:', error.message);
        alert('Failed to insert data.');
        } else {
            message = 'Data inserted successfully!';
            title = '';
            description = '';
            number = '';
            date = '';
            time = '';

            await goto('/table');
        }

        isSubmitting = false;
	};

</script>

<div class="flex flex-col justify-center items-center">
    <form onsubmit={handleSubmit} name="form" class="space-y-4 w-full max-w-md">
        <div class="flex w-full items-center space-x-4">
            <label for="title">Title:</label>
            <input class="input input-bordered w-full" id="title" type="text" bind:value={title} required disabled={isSubmitting}/>
        </div>
    
        <div class="flex w-full items-center space-x-4">
            <label for="description">Description:</label>
            <textarea class="textarea textarea-bordered w-full" id="description" bind:value={description} required disabled={isSubmitting}></textarea>
        </div>

        <div class="flex w-full items-center space-x-4">
            <label for="number">Number:</label>
            <input class="input input-bordered w-full" id="number" type="number" bind:value={number} required disabled={isSubmitting}/>
        </div>
    
        <div class="flex w-full items-center space-x-4">
            <label for="date">Date:</label>
            <input class="input input-bordered w-full" id="date" type="date" bind:value={date} required disabled={isSubmitting}/>
        </div>
    
        <div class="flex w-full items-center space-x-4">
            <label for="time">Time:</label>
            <input class="input input-bordered w-full" id="time" type="time" bind:value={time} required disabled={isSubmitting}/>
        </div>
    
        <div class="flex justify-end w-full">
            <button class="btn btn-primary" type="submit" disabled={isSubmitting}>Submit</button>
        </div>
    </form>
</div>