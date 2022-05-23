
<script>
    import Person from '../Person/ListItem.svelte';
    import PersonCard from '../Person/Card.svelte';
    import { fade, fly } from 'svelte/transition';
    import { flip } from 'svelte/animate';

    let activePersonCard = null;
    export let results = [];

    function hidePersonCard () {
        activePersonCard = null;
    }

    function showPersonCard (person){
        activePersonCard = person
    }

    function transformGroupName (name) {
        return name === 'member' ? 'Members' : name === 'prospect' ? 'Prospects' : 'Staff'
    }

</script>
    <div class="flex flex-col-reverse sm:flex-row absolute top-full bg-white z-50 min-w-full shadow-lg rounded-b-md" on:mouseleave="{hidePersonCard}">

        <div class="w-full max-h-screen overflow-y-scroll" transition:fly={{y:10, duration: 500}}>
            {#each Object.entries(results) as [key, value] (key)}
                <ul animate:flip={{duration: 500}} class="flex flex-col gap-2">
                    <h3 class="text-gray-500 px-2 py-3">
                        ({transformGroupName(key)} {results[key].length})
                    </h3>
                    {#each value as item (item.id)}
                        <li animate:flip={{duration: 500}} class="p-2 hover:bg-gray-100 hover:cursor-pointer" on:mousemove={() => showPersonCard(item)}>
                            <Person {...item}/>
                        </li>
                    {/each}
                </ul>
                {:else}
                <div class="p-2 font-light text-gray-500">No reasults found</div>
            {/each}
        </div>

        {#if activePersonCard}
            <div class="px-2 py-4 sm:py-8 sm:px-12 sm:border-l border-gray-300 w-full" transition:fade={{duration: 500}}>
               <PersonCard {...activePersonCard}/>
            </div>
        {/if}

    </div>