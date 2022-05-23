<script>
    import Avatar from './Avatar.svelte';

    export let first_name = "";
    export let last_name = "";
    export let avatar = "";
    export let membership = "";
    export let email_address = "";
    export let id = Date.now();
    export let active = false;
    export let size = "small";
</script>


<div class="flex flex-wrap gap-2 items-center">
    {#if avatar}
        <Avatar {active} {avatar} {membership} {size}/>
    {/if}
    {#if first_name || last_name}
        <p>{first_name} {last_name}</p>
    {/if}
    {#if id}
        <p class="text-gray-700 font-light">{id}</p>
    {/if}
    {#if email_address}
        <p class="text-gray-700 font-light">{email_address}</p>
    {/if}
</div>
