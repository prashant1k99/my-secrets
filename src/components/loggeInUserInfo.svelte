<script lang="ts">
  export let shareURL: string
  export let qrImage: string

  const copyShareLink = () => {
    navigator.clipboard.writeText(shareURL)
  }

  const toggleTooltip = () => {
    const tooltip = document.querySelector('.tooltip-open')
    if (tooltip) {
      tooltip.classList.toggle('tooltip-open')
    }
  }
</script>

<div class="w-full h-full max-w-screen overflow-hidden sm:pt-8">
  <div class="flex flex-col justify-center items-center h-full">
    <div class="flex flex-col justify-center items-center gap-2">
      <p class="text-2xl font-bold text-primary" id="qr">Scan this QR code to connect</p>
      <div class="w-64 h-64 text-primary my-2" data-background="text-accent" data-foreground="text-primary">
        {#if qrImage}
          <img src={qrImage} alt="QR code" />
        {:else}
          <p class="text-xl font-normal text-accent">Loading...</p>
        {/if}
      </div>
      <p class="text-2xl font-normal text-primary">Or share this link</p>
      <!-- <p class="text-xl font-normal text-accent">{shareURL}</p> -->
      <div class="tooltip" data-tip="Click to Copy link">
        <button class="border border-slate-800 rounded-lg bg-neutral p-2 bg-background max-w-full " on:mouseover={toggleTooltip} on:focus={toggleTooltip} on:click={copyShareLink}>
          <pre class="text-xl font-normal text-accent" >{shareURL}</pre>
        </button>
      </div>
    </div>
  </div>
</div>