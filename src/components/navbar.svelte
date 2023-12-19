<script lang="ts">
  // import GiTripleLock from 'svelte-icons/gi/GiTripleLock.svelte'
  import GiSherlockHolmes from 'svelte-icons/gi/GiSherlockHolmes.svelte'
  import ThemeToggle from './themeToggle.svelte';
</script>

<div class="sm:py-4 p-0 sm:my-2 m-0">
  <div class="container m-auto flex justify-between navbar bg-neutral text-neutral-content p-4 rounded-none sm:rounded-2xl">
    <div class="w-9 h-9 text-primary">
      <!-- <GiTripleLock /> -->
      <GiSherlockHolmes />
    </div>
    <ThemeToggle />
  </div>
</div>
