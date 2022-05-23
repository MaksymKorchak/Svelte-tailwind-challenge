
<script>
    export let searchQuery = '';
    export let fetchResults = () => "";
    export let clearSearchQuery = () => ""
</script>

<label for="search" class="bg-white relative">
    <input 
        bind:value="{searchQuery}" 
        class="w-full px-3 py-2 rounded-md shadow-sm placeholder-black focus:outline-gray-300 disabled:placeholder-gray-300"
        name="search"
        placeholder="Search"
        type="text" 
        on:input="{fetchResults}">

        {#if searchQuery}
            <img on:click="{clearSearchQuery}" src="./images/icons/cross.svg" alt="cross" class="absolute top-1/2 cursor-pointer transform -translate-y-1/2 right-3">
        {:else}
            <img src="./images/icons/search.svg" alt="search" class="absolute top-1/2 transform -translate-y-1/2 right-3">
        {/if}
</label>

