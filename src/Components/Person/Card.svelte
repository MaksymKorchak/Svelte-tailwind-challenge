<script>
    import Avatar from './Avatar.svelte';

    export let first_name = "";
    export let last_name = "";
    export let avatar = "";
    export let membership = "";
    export let email_address = "";
    export let phone =""
    export let id = Date.now();
    export let active = false;
    export let size = "medium";
</script>

<div>
    <div class="flex flex-col items-center mx-auto pb-4 mb-4 border-b border-gray-300">
        {#if avatar}
            <Avatar {active} {avatar} {membership} {size}/>
        {/if}
        {#if first_name || last_name}
            <p>{first_name} {last_name}</p>
        {/if}
        {#if id}
            <p class="text-gray-700 font-light">{id}</p>
        {/if}
    </div>
    <table>
        {#if membership}
            <tr>
                <td>Membership</td>
                <td><span class="ml-2 font-bold">{membership}</span></td>
            </tr>
        {/if}
        {#if phone}
            <tr>
                <td>Phone</td>
                <td><span class="ml-2 font-light">{phone}</span></td>
            </tr>
        {/if}
        {#if email_address}
            <tr>
                <td>Email</td>
                <td><span class="ml-2 text-teal-500">{email_address}</span></td>
            </tr>
        {/if}
    </table>
    <div class="flex justify-around gap-2 flex-wrap pt-4">
        <a href="#" class="w-10 h-10 bg-gray-100 rounded-full flex justify-center items-center">
            <img src="./images/icons/message.svg" alt="message">
        </a>
        <a href="#" class="w-10 h-10 bg-gray-100 rounded-full flex justify-center items-center">
            <img src="./images/icons/phone.svg" alt="phone">
        </a>
        <a href="#" class="w-10 h-10 bg-gray-100 rounded-full flex justify-center items-center">
            <img src="./images/icons/gym.svg" alt="gym">
        </a>
        <a href="#" class="w-10 h-10 bg-gray-100 rounded-full flex justify-center items-center">
            <img src="./images/icons/location.svg" alt="location">
        </a>
    </div>
</div>
    
