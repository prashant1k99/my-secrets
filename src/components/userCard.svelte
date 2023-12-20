<script lang="ts">
  export let name: string
  export let email: string
  export let isOnline: boolean
  export let profilePic: string
  export let lastSeen
</script>

<li class={`flex justify-between gap-x-6 p-4 rounded-xl bg-blend-screen ${isOnline ? 'hover:bg-neutral group' : 'opacity-50'}`}>
  <div class="flex min-w-0 gap-x-4">
    {#if profilePic}
      <img class="h-12 w-12 flex-none rounded-full bg-gray-50" src={profilePic} alt={name + ' profile pic'}>
    {/if}
    <div class="min-w-0 flex-auto">
      <p class="text-lg font-bold leading-6 text-primary">{name}</p>
      <p class="mt-1 truncate text-md font-semibold leading-5 text-base-800 group-hover:text-accent">{email}</p>
    </div>
  </div>
  <div class="hidden group-hover:flex shrink-0 sm:flex sm:flex-col sm:items-end">
    {#if !isOnline && lastSeen}
      <p class="mt-1 text-xs leading-5 text-gray-500 group-hover:hidden">Last seen <time datetime="2023-01-23T13:23Z">{lastSeen}</time></p>
    {/if}

    {#if isOnline}
      <div class="mt-1 flex items-center gap-x-1.5 group-hover:hidden">
        <div class="flex-none rounded-full bg-emerald-500/20 p-1">
          <div class="h-1.5 w-1.5 rounded-full bg-emerald-500"></div>
        </div>
        <p class="text-xs leading-5 text-gray-500">Online</p>
      </div>
      <button class="btn btn-primary py-2 rounded-lg text-base-800 cursor-pointer hidden group-hover:block">Connect</button>
    {/if}
  </div>
</li>