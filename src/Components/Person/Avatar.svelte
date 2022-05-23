<script>
    export let active = false;
    export let avatar = "";
    export let membership = "";
    export let size = "small";
</script>

<div class="relative {size === 'small' ? 'w-7 h-7' : 'w-14 h-14'}">
    <img class="object-cover rounded-full p-0.5 border-2" 
         class:border-yellow-700={membership === 'GOLD'}
         class:border-gray-700={membership === 'SILVER'}
         class:border-purple-700={membership === 'PLATIN'}
         src="./images/avatars/{size}/{avatar}" alt="{avatar}" 
         loading="lazy">
    <div class="absolute right-0.5 bottom-0 p-0.5 rounded-full border border-white {size === 'small' ? 'w-1.5 h-1.5' : 'w-4 h-4'} {active ? 'bg-green-300' : 'bg-red-300'}"></div>
</div>