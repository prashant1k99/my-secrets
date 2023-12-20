<script lang="ts">
  export let shareURL: string
  export let qrImage: string

  let isTextCopied = false
  let copyText = 'Click to Copy'
  
  const toggleTooltip = () => {
    const tooltip = document.querySelector('.tooltip-open')
    if (tooltip) {
      tooltip.classList.toggle('tooltip-open')
    }
  }

  const copyShareLink = () => {
    navigator.clipboard.writeText(shareURL)
    isTextCopied = true
    copyText = 'Copied'
    toggleTooltip()
    setTimeout(() => {
      isTextCopied = false
      copyText = 'Click to Copy'
      toggleTooltip()
    }, 3000);
  }
</script>

<div class="w-full h-full max-w-screen overflow-hidden sm:pt-8">
  <div class="flex flex-col justify-center items-center h-full w-full">
    <div class="flex flex-col justify-center items-center gap-2 w-full">
      <p class="text-2xl font-bold text-primary" id="qr">Scan this QR code to connect</p>
      <div class="w-64 h-64 text-primary my-2" data-background="text-accent" data-foreground="text-primary">
        {#if qrImage}
          <img src={qrImage} alt="QR code" />
        {:else}
          <p class="text-xl font-normal text-accent">Loading...</p>
        {/if}
      </div>
      <p class="text-2xl font-normal text-primary">Or share this link</p>
      <div class="flex border border-slate-800 bg-neutral max-w-full px-8 py-2 rounded-lg w-full items-center">
        <input disabled class="text-accent w-full text-xl bg-inherit rounded-lg text-ellipsis overflow-hidden mr-2" value={shareURL} />
        <div class="tooltip" data-tip={copyText}>
          <button type="button" on:click={copyShareLink}>
            {#if isTextCopied}
            <svg class="w-4 h-4 text-accent" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"/></svg>
            {:else}
            <svg class="w-4 h-4 text-accent group-hover:rotate-6 transition" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="8" height="4" x="8" y="2" rx="1" ry="1"/><path d="M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2"/></svg>
            {/if}
          </button>
        </div>
      </div>
    </div>
  </div>
</div>