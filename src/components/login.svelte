<script lang="ts">
  import FaGoogle from 'svelte-icons/fa/FaGoogle.svelte'
</script>

<div class="hero h-full">
  <div class="hero-content text-center">
    <div class="flex flex-col max-w-xl h-full">
      <h1 class="text-5xl font-bold">Authorize</h1>
      <p class="py-6">Have secret conversation, share top secret files that will not be stored on any server and every record of it will be deleted once you've seen it.
        <br/>
        Everything is End-to-End Encrypted, giving you the ensurity of your chat not being leaked.</p>
      <button class="btn btn-accent rounded-lg max-w-md m-auto">
        <span class="h-6 text-neutral">
          <FaGoogle />
        </span>
        Continue With Google
      </button>
    </div>
  </div>
</div>